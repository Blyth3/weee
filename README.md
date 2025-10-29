# TALAS Reading Assessment System - Requirements Document

## System Overview

**System Name:** TALAS (Teaching and Learning Assessment System) - Reading Assessment System  
**Version:** v1.0  
**Framework:** Laravel 11  
**Database:** MySQL/SQLite  
**Purpose:** Comprehensive reading assessment platform for educational institutions in Region 1, Philippines

---

## 1. FUNCTIONAL REQUIREMENTS

### 1.1 User Management & Authentication

#### 1.1.1 User Roles (Hierarchical Structure)
- **CLMD Coordinator** (`clmd_coordinator`)
  - Highest level access control
  - Can manage all regions
  - Can create Division Coordinators
  - Full system administration capabilities
  
- **Division Coordinator** (`division_coordinator`)
  - Regional oversight role
  - Must be assigned to a specific division
  - Can create District Coordinators
  - Manages users within their division
  
- **District Coordinator** (`district_coordinator`)
  - District oversight role
  - Must be assigned to a specific district
  - Can create School Coordinators
  - Manages users within their district
  
- **School Coordinator** (`school_coordinator`)
  - School-level oversight
  - Must be assigned to a specific school
  - Can create Teachers
  - Manages teachers within their school
  
- **Teacher** (`teacher`)
  - Classroom level access
  - Must be assigned to a specific school
  - Conducts reading assessments
  - Manages students and classes

#### 1.1.2 Authentication Features
- User login with email and password
- Password encryption using Laravel hashing
- Remember token functionality for persistent login
- Terms of Service acceptance requirement on first login
- Password reset functionality (no email verification required)
- Logout capability
- Session management

#### 1.1.3 User Account Management
- Create new user accounts
- Edit existing user information
- Deactivate user accounts (soft delete)
- Reactivate deactivated accounts
- View user profiles
- Profile picture management (Base64 storage)
- Email uniqueness validation
- Role-based user creation (hierarchical permissions)
- User creation tracking (created_by field)
- Search and filter users by name, email, or role
- Export user data to CSV format

#### 1.1.4 Location-Based Access Control
- Users must be assigned to appropriate locations based on role:
  - Teachers: division_id, district_id, school_id
  - School Coordinators: division_id, district_id, school_id
  - District Coordinators: division_id, district_id
  - Division Coordinators: division_id
  - CLMD Coordinators: No location required
- Data isolation based on user's location assignment
- Automatic filtering of data based on hierarchical scope
- Location hierarchy: Region → Division → District → School

### 1.2 Location Management

#### 1.2.1 Hierarchical Structure
- **Region Management**
  - Create, read, update, delete regions
  - Currently supports Region 1 only
  - Region-to-Division relationships
  
- **Division Management**
  - Create, read, update, delete divisions
  - Link to parent region
  - Division-to-District relationships
  
- **District Management**
  - Create, read, update, delete districts
  - Link to parent division
  - District-to-School relationships
  
- **School Management**
  - Create, read, update, delete schools
  - Link to parent district
  - School-to-Class relationships
  - Active/Inactive status management

#### 1.2.2 Location Data APIs
- Get all regions: `/api/regions`
- Get divisions by region: `/api/divisions/{region}`
- Get districts by division: `/api/districts/{division}`
- Get schools by district: `/api/schools/{district}`

### 1.3 Student Management

#### 1.3.1 Student Profile Management
- Create student profiles with:
  - Student ID
  - First name
  - Last name
  - Grade level (limited to Grade 11 and 12)
  - Class assignment
  - School assignment
  - Active/Inactive status
  - Strand (optional)
- Edit student information
- Delete student records
- View student profile
- Search and filter students

#### 1.3.2 Student-Class Relationship
- Assign students to classrooms
- View students by class
- Unassign students from classes
- Track student movement between classes
- Class attendance tracking

#### 1.3.3 Student Assessment Tracking
- Track assessment history per student
- Prevent duplicate assessments (same test type for same material)
- View student performance over time
- Check if student has taken specific test type
- Get all assessments for specific student and library

### 1.4 Classroom Management

#### 1.4.1 Classroom Operations
- Create classrooms with:
  - Class name
  - Grade level
  - Section
  - Teacher assignment
  - School assignment
- Edit classroom information
- Archive classrooms (soft delete)
- Unarchive archived classrooms
- Delete classrooms
- View classroom details
- List active classrooms
- List archived classrooms

#### 1.4.2 Class-Student Management
- View all students in a class
- Add students to class
- Remove students from class
- Track class capacity
- Monitor unassessed students

### 1.5 Reading Material Management (Library)

#### 1.5.1 Material Creation
- Upload reading materials with:
  - Title
  - Description
  - Reading passage text
  - File upload (PDF, DOC, DOCX, TXT)
  - File size limit: 10MB
  - Category selection
  - Test type selection (Pre-test, Post-test)
  - Grade level specification (Grade 11, Grade 12)
  - Uploader tracking
- Validate file types and sizes
- Store file metadata

#### 1.5.2 Material Management
- View all materials
- Search and filter materials
- Edit material details
- Activate/Deactivate materials
- Archive materials (with reason)
- Unarchive materials
- Delete materials
- Download material files
- Export library data

#### 1.5.3 Question Management
- Add multiple choice questions to materials
- Minimum 1 question per material
- Question format:
  - Question text
  - 4 answer options (A, B, C, D)
  - Correct answer designation
- Edit existing questions
- Delete questions
- View all questions for a material
- Validation of question completeness

### 1.6 Assessment System

#### 1.6.1 Assessment Workflow
The system follows a structured 4-step assessment process:

**Step 1: Material Selection**
- Teachers select appropriate reading material
- Material must match student's grade level
- Material must be active and not archived

**Step 2: Class and Student Selection**
- Select classroom
- Select student(s) for assessment
- Check if student has already taken the test type

**Step 3: Reading Phase**
- Student reads the assigned passage
- No time limit for reading phase
- Teacher monitors progress

**Step 4: Reading Level Evaluation**
- Teacher evaluates student's reading progression:
  - Word Level: Basic word recognition
  - Phrase Level: Simple phrase reading
  - Sentence Level: Complete sentence reading
  - Paragraph Level: Full paragraph comprehension
- Must follow progression sequence (word → phrase → sentence → paragraph)
- Cannot skip levels

**Step 5: Comprehension Questions**
- Triggered only if student reaches "Paragraph Level"
- Multiple choice format (A, B, C, D)
- Minimum 1 question per material
- Teacher records student answers

**Step 6: Results Display**
- Automatic scoring calculation
- Performance level classification
- Results display to teacher

#### 1.6.2 Assessment Constraints
- Grade Levels: Only Grade 11 and 12 supported
- Test Types: Pre-test and Post-test only
- Duplicate Prevention: Students cannot take the same test type twice for the same material
- Reading Level Progression: Must follow word → phrase → sentence → paragraph sequence
- Questions: Only appear if student reaches paragraph level

#### 1.6.3 Assessment Scoring
- Score Calculation: Number of correct answers
- Maximum Score: Total number of questions
- Percentage Calculation: (Score / Max Score) × 100
- Performance Classification:
  - **Independent Level**: 8+ correct answers
  - **Instructional Level**: 5-7 correct answers
  - **Frustration Level**: 0-4 correct answers

#### 1.6.4 Assessment Data Storage
- Student assessment records with:
  - Library reference
  - Student reference
  - Classroom reference
  - Teacher reference
  - Grade level
  - Assessment type
  - Test type (pre-test/post-test)
  - Reading level achieved
  - Score and percentage
  - Performance level
  - Assessment date
  - Completion timestamp
  - Evaluation notes (optional)

#### 1.6.5 Assessment Results Management
- View individual assessment results
- View all results for a teacher
- Filter results by date range
- Filter results by student
- Filter results by material
- Filter results by grade level
- Export assessment data
- Track assessment history
- View performance trends

### 1.7 Dashboard & Reporting

#### 1.7.1 Dashboard Features by Role

**Teacher Dashboard**
- Total students in their classes
- Total assessments conducted
- Recent assessments
- Student performance overview
- Reading level trends
- Performance distribution (Independent/Instructional/Frustration)
- Unassessed students tracking

**School Coordinator Dashboard**
- School-wide performance metrics
- Total teachers and students
- Assessment statistics for their school
- Teacher activity monitoring
- Student assessment tracking
- Performance trends
- Unassessed students list
- Comparative analysis within school

**District Coordinator Dashboard**
- District-wide performance overview
- Total schools, teachers, and students
- School comparison metrics
- Assessment statistics for their district
- Regional performance trends
- Performance distribution across schools
- Unassessed students across district
- Comparative analysis between schools

**Division Coordinator Dashboard**
- Division-wide comprehensive reports
- District performance comparison
- Total districts, schools, teachers, students
- System-wide statistics for their division
- Advanced trend analysis
- Performance distribution across districts
- Unassessed students tracking
- Comparative analysis between districts

**CLMD Coordinator Dashboard**
- Complete system overview
- All regions, divisions, and districts
- Comprehensive performance metrics
- System administration tools
- Total students, teachers, assessments
- Overall system trends
- Performance distribution across all levels
- Export capabilities
- Advanced analytics

#### 1.7.2 Statistical Analysis Features
- Trend calculations using linear regression
- Performance metric calculations
- Automatic improvement percentage calculations
- Correlation coefficient calculation
- Slope calculation (least squares method)
- Data validation for statistical accuracy
- Minimum data requirements (3 points for reliable trends)
- Monthly trend tracking
- Reading level trend analysis
- Grade-specific data analysis

#### 1.7.3 Reporting Capabilities
- Export comprehensive data to CSV
- Role-based filtered exports
- Date-stamped file generation
- Export system-wide data
- Export filtered data by location
- Export user data
- Export assessment data
- Export library data
- Export activity logs

### 1.8 Activity Logging

#### 1.8.1 Activity Tracking
- Log all user actions
- Track assessment completions
- Track material uploads
- Track user creations
- Track account activations/deactivations
- Track material archiving
- Track question modifications
- Log system errors

#### 1.8.2 Activity Log Features
- View activity logs
- Filter logs by user
- Filter logs by date range
- Filter logs by activity type
- Export activity logs
- Activity log statistics
- Detailed log information

### 1.9 File Management

#### 1.9.1 File Upload Support
- Supported formats: PDF, DOC, DOCX, TXT
- Maximum file size: 10MB per file
- File type validation
- File size validation
- Automatic storage to secure directory
- File metadata storage

#### 1.9.2 File Operations
- Download files
- File serving
- Storage link creation
- Automatic cleanup of old files when updating materials
- Secure file storage

### 1.10 Data Validation & Business Rules

#### 1.10.1 Input Validation
- Email format validation
- Password strength requirements
- Role enum validation
- Location assignment validation
- File type and size validation
- Question format validation
- Reading level progression validation
- Duplicate assessment prevention
- Grade level restrictions

#### 1.10.2 Data Integrity
- Foreign key constraints
- Cascade delete rules
- Unique constraints (email, student IDs)
- Required field validation
- Data range validation
- Null value handling

---

## 2. NON-FUNCTIONAL REQUIREMENTS

### 2.1 Performance Requirements

#### 2.1.1 Response Time
- Page load time: < 3 seconds
- Dashboard loading: < 5 seconds
- Search/filter operations: < 2 seconds
- File upload: < 10 seconds (for max file size)
- Database queries: Optimized for large datasets
- Assessment submission: Near-instantaneous feedback

#### 2.1.2 Scalability
- Support for multiple concurrent users
- Efficient handling of large datasets
- Optimized database queries
- Lazy loading for large lists
- Pagination for data display
- Caching mechanisms for frequent queries

#### 2.1.3 System Capacity
- Support for multiple regions (currently Region 1)
- Support for multiple divisions per region
- Support for multiple districts per division
- Support for multiple schools per district
- Support for multiple classes per school
- Support for multiple students per class
- Support for multiple assessments per student
- Storage capacity for reading materials

### 2.2 Security Requirements

#### 2.2.1 Authentication & Authorization
- Secure password hashing (bcrypt)
- Session-based authentication
- Role-based access control (RBAC)
- Hierarchical permission model
- Location-based data access control
- CSRF protection
- XSS protection
- SQL injection prevention (using ORM)

#### 2.2.2 Data Security
- Encrypted password storage
- Secure file upload handling
- Input sanitization
- Output escaping
- Secure session management
- HTTPS support (recommended)
- Data isolation between hierarchical levels

#### 2.2.3 Access Control
- Unauthorized access prevention
- Privilege escalation prevention
- User deactivation functionality
- Account lockout mechanism
- Audit trail for sensitive operations
- Terms of Service acceptance tracking

### 2.3 Usability Requirements

#### 2.3.1 User Interface
- Intuitive and user-friendly interface
- Consistent navigation across all pages
- Clear error messages
- Helpful validation messages
- Responsive design for different screen sizes
- Modern and professional appearance
- Clear visual hierarchy
- Accessible color schemes

#### 2.3.2 User Experience
- Easy-to-follow assessment workflow
- Clear instructions for each step
- Progress indicators
- Confirmation dialogs for critical actions
- Success/error notifications
- Search and filter capabilities
- Sort functionality
- Export capabilities

#### 2.3.3 Browser Compatibility
- Support for modern web browsers:
  - Google Chrome (latest)
  - Mozilla Firefox (latest)
  - Safari (latest)
  - Microsoft Edge (latest)
- Cross-browser compatibility
- Responsive design for mobile devices

### 2.4 Reliability Requirements

#### 2.4.1 System Availability
- 99% uptime requirement
- Graceful error handling
- Proper exception management
- Transaction rollback for failed operations
- Backup and recovery mechanisms
- Data backup procedures

#### 2.4.2 Error Handling
- Comprehensive error handling
- User-friendly error messages
- Logging of system errors
- Graceful degradation
- Input validation to prevent errors
- Database transaction management

#### 2.4.3 Data Integrity
- Database constraints and validations
- Referential integrity
- Data consistency checks
- Orphaned record prevention
- Cascade delete handling
- Soft delete for important entities

### 2.5 Maintainability Requirements

#### 2.5.1 Code Quality
- Clean and readable code
- Modular architecture
- Separation of concerns
- Code documentation
- Following Laravel best practices
- SOLID principles adherence
- Repository pattern usage

#### 2.5.2 Extensibility
- Easy to add new features
- Modular design
- Configurable settings
- Plugin architecture support
- API endpoints for future integration
- Database migration support

#### 2.5.3 Documentation
- Comprehensive user manual
- Technical documentation
- Deployment guide
- System testing notes
- Code comments
- Database schema documentation
- API documentation

### 2.6 Portability Requirements

#### 2.6.1 Platform Independence
- Web-based application (browser access)
- No client installation required
- Cross-platform compatibility
- Server compatibility (Linux/Windows)

#### 2.6.2 Database Compatibility
- MySQL database support
- SQLite support (development)
- Database migration support
- Database seeders for initial data

#### 2.6.3 Deployment Flexibility
- Simple deployment process
- Environment configuration
- Docker support (optional)
- Cloud deployment ready

### 2.7 Testing Requirements

#### 2.7.1 Testing Types
- Unit testing
- Integration testing
- Feature testing
- Performance testing
- Security testing
- User acceptance testing

#### 2.7.2 Test Coverage
- Core functionality tests
- Authentication tests
- Authorization tests
- Data validation tests
- Business logic tests
- API endpoint tests

### 2.8 Compliance Requirements

#### 2.8.1 Data Privacy
- Personal data protection
- Secure data storage
- Access control to personal information
- Data retention policies
- Terms of Service acceptance

#### 2.8.2 Educational Standards
- Alignment with educational assessment standards
- Grading methodology compliance
- Student progress tracking standards
- Reporting standards

### 2.9 Operational Requirements

#### 2.9.1 Backup & Recovery
- Regular database backups
- File storage backups
- Backup automation
- Recovery procedures
- Data restoration capabilities

#### 2.9.2 Monitoring & Logging
- Error logging
- Activity logging
- Performance monitoring
- User activity tracking
- System health checks

#### 2.9.3 Update & Maintenance
- System update procedures
- Patch management
- Feature updates
- Bug fixes
- Security patches

---

## 3. CONSTRAINTS & LIMITATIONS

### 3.1 Technical Constraints
- PHP 8.1 or higher required
- Laravel 11 framework
- MySQL 5.7+ or SQLite
- Composer dependency management
- Storage space for file uploads

### 3.2 Functional Constraints
- Only Region 1 supported currently
- Only Grade 11 and 12 supported
- Pre-test and Post-test only
- No mid-term assessments
- Maximum 10MB file uploads
- Reading level progression must be sequential
- Questions only appear at paragraph level

### 3.3 Business Constraints
- User creation follows strict hierarchy
- Each role can only create users one level below
- Location assignments are mandatory for most roles
- Terms of Service must be accepted before use
- Assessment duplicates are prevented

### 3.4 Operational Constraints
- Requires stable internet connection
- Browser JavaScript enabled
- Modern web browser required
- Administrator access for deployment
- Database access for migrations

---

## 4. ASSUMPTIONS

1. All users have basic computer literacy
2. Users have stable internet connection
3. Users accept Terms of Service before using the system
4. Teachers conduct assessments in classroom setting
5. File uploads are legitimate educational materials
6. User roles and locations are correctly assigned
7. System is maintained and monitored regularly
8. Regular backups are performed
9. PHP server is properly configured
10. Database is maintained and optimized

---

## 5. GLOSSARY

- **TALAS**: Teaching and Learning Assessment System
- **CLMD**: Curriculum and Learning Management Division
- **Pre-test**: Assessment conducted before instruction
- **Post-test**: Assessment conducted after instruction
- **Reading Level**: Student's progression in reading skills (Word, Phrase, Sentence, Paragraph)
- **Performance Level**: Classification of student performance (Independent, Instructional, Frustration)
- **Strand**: Specialized subject track in Senior High School (e.g., STEM, ABM, HUMSS)
- **Archived**: Soft delete status for preserving data history
- **Region 1**: Ilocos Region in the Philippines
- **Soft Delete**: Marking records as deleted without actually removing them from database

---

*This requirements document covers TALAS v1.0 Reading Assessment System and should be updated as new features are added or modified.*

