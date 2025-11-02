# 📚 TALAS: DATA ANALYTICS FOR READING COMPREHENSION IN FILIPINO - User Manual

**Version:** 1.0  
**System:** TALAS: DATA ANALYTICS FOR READING COMPREHENSION IN FILIPINO 

---

## Table of Contents

1. [How to Log In](#how-to-log-in)
2. [Logging In as Administrator (CLMD Coordinator)](#logging-in-as-administrator-clmd-coordinator)
3. [Logging In as Teacher](#logging-in-as-teacher)
4. [Logging In as Coordinator](#logging-in-as-coordinator)
5. [Quick Reference](#quick-reference)

---

## How to Log In

### Step-by-Step Login Process

1. **Open your web browser** (Chrome, Firefox, Safari, or Edge)
2. **Navigate to the TALAS login page** (URL provided by your administrator)
3. **You will see the login form** with:
   - Email field
   - Password field
   - "Remember me" checkbox (optional)
   - Terms of Service checkbox (required on first login)
   - "Forgot Password?" link
4. **Enter your credentials**:
   - Type your email address
   - Type your password
   - If this is your first login, check the "I accept the Terms of Service" box
5. **Click "Log In"**
6. **You will be redirected to your dashboard** based on your role

### First-Time Login

On your first login:
1. You **must** check the "I accept the Terms of Service" checkbox
2. Read the terms before accepting
3. After logging in, you'll see your dashboard
4. **Recommended**: Go to your profile and change your password

### Default Test Accounts

- **Admin (CLMD Coordinator)**: `admin@talas.com` / `admin123`
- **Division Coordinator**: `michael.brown@talas.com` / `admin123`
- **Teacher**: `john.smith@talas.com` / `admin123`

⚠️ **Important**: Change default passwords in production!

---

## Logging In as Administrator (CLMD Coordinator)

### After Login - What You See

When you log in as **CLMD Coordinator**, you will be redirected to your **Dashboard**.

#### Dashboard Overview

Your dashboard displays:
- **Top Navigation Menu** with options:
  - Dashboard (current page)
  - Library Management
  - User Management
  - Activity Logs
  - Profile (your name with dropdown)

- **Dashboard Statistics Cards** showing:
  - Total Students (across all regions)
  - Total Teachers
  - Total Assessments
  - Performance metrics

- **Charts and Graphs**:
  - Performance distribution
  - Assessment trends
  - Regional comparisons

---

### Workflow 1: Managing the Library (Reading Materials)

#### Step 1: Access Library Management

1. **Click "Library Management"** in the top navigation menu
2. **You will see** a page showing:
   - List of all reading materials (active and archived)
   - Search bar to find materials
   - Filter options (by grade level, test type, status)
   - "Create New Material" button at the top

#### Step 2: Create a New Reading Material

1. **Click the "Create New Material" button**
2. **Fill in the form**:
   - **Title**: Enter a descriptive title (e.g., "Grade 11 Pre-Test - Short Story")
   - **Passage Text**: Paste or type the full reading passage here
   - **Grade Level**: Select either "11" or "12" from dropdown
   - **Test Type**: Select "Pre-test" or "Post-test"
   - **Description**: Optional - add any notes about the material
   - **Upload File**: Click "Choose File" and select a PDF, DOC, DOCX, or TXT file (max 10MB)
3. **Click "Create Material"**
4. **You will be redirected** to the material management page where you can add questions

#### Step 3: Add Questions to the Material

1. **After creating the material**, you'll see a page with:
   - Material details at the top
   - "Add Questions" section below
2. **To add a question**:
   - **Question Text**: Type your question
   - **Option A**: Enter first answer choice
   - **Option B**: Enter second answer choice
   - **Option C**: Enter third answer choice
   - **Option D**: Enter fourth answer choice
   - **Correct Answer**: Select which option (A, B, C, or D) is the correct answer
   - Click **"Add Question"**
3. **Repeat Step 2** for each question (minimum 1 question required)
4. **Questions appear** in a list below, showing:
   - Question number
   - Question text
   - All 4 options
   - Correct answer highlighted
   - Edit and Delete buttons

#### Step 4: Manage Existing Materials

**To View/Edit a Material**:
1. In Library Management, **find the material** in the list
2. **Click on the material title** or click "View"
3. You'll see:
   - Material details
   - Associated file (with download link)
   - List of questions
   - Edit and Delete buttons

**To Edit a Material**:
1. Click **"Edit"** button
2. Modify any field (title, passage, grade level, test type, file)
3. Click **"Save Changes"**

**To Edit a Question**:
1. Find the question in the material's question list
2. Click **"Edit"** next to the question
3. Modify question text, options, or correct answer
4. Click **"Save Changes"**

**To Delete a Question**:
1. Click **"Delete"** next to the question
2. Confirm deletion
   ⚠️ Note: You cannot delete the last remaining question

**To Archive a Material**:
1. Click **"Archive"** button next to the material
2. Archived materials are hidden from teachers but not deleted
3. To restore: Use filter to show "Archived", then click **"Unarchive"**

**To Activate/Deactivate**:
- **Deactivate**: Makes material unavailable to teachers (they won't see it)
- **Activate**: Makes material available again

---

### Workflow 2: Managing Users

#### Step 1: Access User Management

1. **Click "User Management"** in the top navigation menu
2. **You will see**:
   - List of Division Coordinators you've created
   - Search bar to find users
   - Filter options
   - "Create User" button

#### Step 2: Create a New User (Division Coordinator)

1. **Click "Create User" button**
2. **Fill in the form**:
   - **Name**: Enter full name
   - **Email**: Enter unique email address
   - **Password**: Enter initial password (minimum 8 characters)
   - **Role**: Select "Division Coordinator" (this is the only role you can create)
   - **Division**: Select from dropdown (required for Division Coordinator)
3. **Click "Create User"**
4. **The new user** will appear in your user list
   ⚠️ **Important**: Inform the new user of their login credentials separately

#### Step 3: View and Manage Users

**To View User Details**:
- Click on a user's name or email in the list
- View their profile, activity, and created users

**To Edit a User**:
1. Click **"Edit"** next to the user
2. Update information (name, email, password if needed)
3. Click **"Save Changes"**

**To Deactivate a User**:
1. Click **"Deactivate"** next to the user
2. Confirm the action
3. User cannot log in, but data is preserved

**To Reactivate a User**:
1. Filter by "Deactivated" status
2. Click **"Reactivate"** next to the user
3. User can log in again

---

### Workflow 3: Viewing Activity Logs

#### Step 1: Access Activity Logs

1. **Click "Activity Logs"** in the top navigation menu
2. **You will see**:
   - List of all system activities
   - Filters (by date, user, action type)
   - Export button

#### Step 2: Review Activities

- Each log entry shows:
  - Timestamp
  - User who performed action
  - Action type (login, create, update, delete)
  - Resource affected
  - Details

#### Step 3: Export Logs

1. **Click "Export Activity Logs"**
2. Select date range (optional)
3. CSV file downloads automatically

---

### Workflow 4: Dashboard Overview

#### What You Can See

When you're on the dashboard:

1. **Statistics Overview**:
   - Total students in the system
   - Total teachers
   - Total assessments completed
   - Performance breakdowns

2. **Charts and Visualizations**:
   - Performance distribution (pie chart)
   - Assessment trends over time (line chart)
   - Regional comparisons
   - Pre-test vs Post-test improvements

3. **Quick Actions**:
   - Access to all major sections

---

## Logging In as Teacher

### After Login - What You See

When you log in as **Teacher**, you will be redirected to your **Dashboard**.

#### Dashboard Overview

Your dashboard displays:
- **Top Navigation Menu** with:
  - Dashboard (current page)
  - Reading Materials
  - My Classes
  - Assessment Results
  - Unassessed Students
  - Profile (your name with dropdown)

- **Dashboard Statistics** showing:
  - Your total students
  - Your total classes
  - Completed assessments
  - Students needing assessment
  - Performance distribution for your students

- **Charts**:
  - Your students' performance trends
  - Reading level progression
  - Assessment completion status

---

### Workflow 1: Managing Your Classes

#### Step 1: Access My Classes

1. **Click "My Classes"** in the top navigation menu
2. **You will see**:
   - List of your active classes
   - "Create New Class" button
   - Filter options (active/archived)

#### Step 2: Create a New Class

1. **Click "Create New Class" button**
2. **Fill in the form**:
   - **Class Name**: Enter name (e.g., "Grade 11 - Section A")
   - **Grade Level**: Select "11" or "12" from dropdown
   - **Section**: Enter section identifier (optional)
   - **Subject**: Enter subject name (optional)
   - **Description**: Add any notes (optional)
3. **Click "Create Class"**
4. **Your new class** appears in the classes list

#### Step 3: View Class Details and Manage Students

1. **Click on a class name** in the list
2. **You will see**:
   - Class information
   - List of students in this class
   - "Add Student" button
   - "Edit Class" and "Delete Class" buttons

#### Step 4: Add Students to a Class

1. **Click "Add Student" button**
2. **Fill in the form**:
   - **First Name**: Enter student's first name
   - **Last Name**: Enter student's last name
   - **Student ID**: Enter ID number (optional)
   - **Notes**: Any additional information (optional)
3. **Click "Add Student"**
4. **Student appears** in the class roster

#### Step 5: Edit Student Information

1. **Find the student** in the class roster
2. **Click "Edit"** next to the student's name
3. **Update information** (name, ID, notes)
4. **Click "Save Changes"**

#### Step 6: Delete a Student

⚠️ **Warning**: This will also delete the student's assessment records.

1. **Click "Delete"** next to the student
2. **Confirm deletion**
3. Student is permanently removed

#### Step 7: Archive or Delete a Class

**To Archive a Class**:
1. **Click "Archive"** next to the class
2. Class is hidden but not deleted
3. To restore: Filter by "Archived", then click **"Unarchive"**

**To Delete a Class**:
⚠️ **Warning**: This deletes the class and ALL student data and assessments.

1. **Click "Delete"** next to the class
2. **Confirm deletion**
3. Class is permanently removed

---

### Workflow 2: Accessing Reading Materials

#### Step 1: View Available Materials

1. **Click "Reading Materials"** in the top navigation menu
2. **You will see**:
   - Cards showing available reading materials
   - Filter options:
     - **Test Type**: Pre-test or Post-test dropdown
     - **Grade Level**: Filter by grade (only shows grades you teach)
   - Each material card shows:
     - Title
     - Grade level
     - Test type
     - Number of questions
     - Upload date

#### Step 2: View Material Details

1. **Click on a material card**
2. **You will see**:
   - Full material information
   - Passage text
   - Download button (for PDF/DOC file if available)
   - Preview of questions
   - "Start Assessment" button

#### Step 3: Download Material File

1. **Click "Download"** button on material details page
2. **File downloads** to your device (PDF, DOC, DOCX, or TXT)
3. **You can print or share** this file with students

---

### Workflow 3: Conducting an Assessment

This is a **4-step process** that must be completed in one session.

#### Step 1: Select Material and Start Assessment

1. **Go to Reading Materials**
2. **Click on a material** you want to use
3. **Click "Start Assessment"** button
4. **Select Class**:
   - Choose the class from dropdown
   - Only classes matching the material's grade level are shown
5. **Select Students**:
   - Check boxes next to individual students, OR
   - Select "Select All" checkbox
   - ⚠️ Students who already took this test type are disabled (cannot select)
6. **Click "Continue to Assessment"**

#### Step 2: Reading Phase

1. **Present the material** to the student:
   - Show on screen, OR
   - Print/download the file
2. **Let the student read** at their own pace
   - **No time limit** - don't rush
3. **Monitor the student** as they read
4. **When student finishes reading**, click **"Student Has Finished Reading"** button
5. **System proceeds** to next phase

#### Step 3: Reading Level Evaluation

1. **Based on your observation**, evaluate the student's reading:
   - **Word Level**: Can read individual words
   - **Phrase Level**: Can read short phrases
   - **Sentence Level**: Can read complete sentences
   - **Paragraph Level**: Can read paragraphs with comprehension
2. **Select the highest level** the student achieved
   - ⚠️ Levels must progress: Word → Phrase → Sentence → Paragraph
3. **Click "Continue"**

**What Happens Next**:
- If student reached **Paragraph Level**: System proceeds to questions
- If student did **NOT** reach Paragraph Level: Assessment ends here (no questions)

#### Step 4: Comprehension Questions

**Note**: This step only appears if student reached Paragraph Level.

1. **Questions appear** on screen (one at a time or all together)
2. **For each question**:
   - Read the question to the student
   - Select the student's answer (A, B, C, or D)
   - Move to next question
3. **Review all answers** before submitting
4. **Click "Submit Assessment"** when done
5. **Results page appears** immediately showing:
   - Reading level achieved
   - Number of questions answered
   - Number correct
   - Performance level (Independent/Instructional/Frustration)
   - Score percentage

**Performance Levels**:
- **Independent Level**: 8+ correct answers
- **Instructional Level**: 5-7 correct answers
- **Frustration Level**: 0-4 correct answers

---

### Workflow 4: Viewing Assessment Results

#### Step 1: View All Results

1. **Click "Assessment Results"** in the top navigation menu
2. **You will see**:
   - List of all completed assessments
   - Filters:
     - By class
     - By student name
     - By date range
     - By test type (Pre-test/Post-test)
   - Each result shows:
     - Student name
     - Material title
     - Test type
     - Date completed
     - Reading level
     - Score and performance level

#### Step 2: View Individual Assessment Details

1. **Click on a result** in the list
2. **You will see**:
   - Full assessment details
   - Student information
   - Material used
   - Reading level achieved
   - All questions with student's answers
   - Correct/incorrect indicators
   - Final score and performance classification

#### Step 3: Export Results

1. **Use filters** to select specific results (optional)
2. **Click "Export"** button
3. **CSV file downloads** with all filtered results

---

### Workflow 5: Tracking Unassessed Students

#### Step 1: Access Unassessed Students

1. **Click "Unassessed Students"** in the top navigation menu
2. **You will see**:
   - List of students who need assessment
   - Filters:
     - By test type (Pre-test, Post-test, or Both)
     - By class
     - By grade level

#### Step 2: Use the List

- **See which students** haven't taken:
  - Pre-test only
  - Post-test only
  - Neither test
- **Click on a student** to view their details
- **Use this list** to ensure all students are assessed

---

### Workflow 6: Viewing Your Dashboard

#### What Your Dashboard Shows

1. **Quick Statistics**:
   - Total Students (in all your classes)
   - Total Classes
   - Completed Assessments
   - Unassessed Students count

2. **Performance Charts**:
   - Your students' reading level distribution
   - Pre-test vs Post-test comparison
   - Improvement trends
   - Performance by class

3. **Quick Actions**:
   - Links to create new class
   - Links to start new assessment
   - Links to view results

---

## Logging In as Coordinator

Coordinators have different levels: School Coordinator, District Coordinator, and Division Coordinator. They have similar workflows with different scopes.

### After Login - What You See

When you log in as any **Coordinator**, you will be redirected to your **Dashboard**.

#### Dashboard Overview

Your dashboard shows:
- **Top Navigation Menu** with:
  - Dashboard
  - User Management
  - Unassessed Students (School and District Coordinators)
  - Profile

- **Dashboard Statistics** for your scope:
  - Total students in your scope
  - Total teachers/coordinators you manage
  - Total assessments
  - Performance metrics

- **Charts**:
  - Performance trends for your scope
  - Comparison charts (by school/district if applicable)

---

### Workflow 1: Managing Users (Creating Users)

**Who can create what**:
- **School Coordinator** → Creates **Teachers**
- **District Coordinator** → Creates **School Coordinators**
- **Division Coordinator** → Creates **District Coordinators**

#### Step 1: Access User Management

1. **Click "User Management"** in the top navigation menu
2. **You will see**:
   - List of users you've created (only one level below you)
   - Search bar
   - "Create User" button

#### Step 2: Create a New User

1. **Click "Create User" button**
2. **Fill in the form**:
   - **Name**: Enter full name
   - **Email**: Enter unique email
   - **Password**: Enter initial password (min 8 characters)
   - **Role**: Select the role you can create (dropdown shows only your allowed roles)
   - **Location Assignments**: 
     - If creating **Teacher** or **School Coordinator**: Select Division, District, and School
     - If creating **District Coordinator**: Select Division and District
     - If creating **Division Coordinator**: Select Division only
3. **Click "Create User"**
4. **User appears** in your list
   ⚠️ **Important**: Inform the new user of their credentials separately

#### Step 3: Manage Existing Users

**To Edit**:
- Click "Edit" next to user
- Update information
- Save changes

**To Deactivate**:
- Click "Deactivate" next to user
- User cannot log in but data is preserved

**To Reactivate**:
- Filter by "Deactivated"
- Click "Reactivate"

---

### Workflow 2: Viewing Reports and Dashboard

#### What Your Dashboard Shows

**School Coordinator Dashboard**:
- School-wide statistics
- Teacher activity
- Student assessment completion
- Performance trends for your school
- Unassessed students list

**District Coordinator Dashboard**:
- District-wide overview
- School comparison metrics
- Teacher and student statistics across all schools in district
- Performance by school

**Division Coordinator Dashboard**:
- Division-wide comprehensive reports
- District performance comparison
- All statistics for your division
- Advanced trend analysis

#### Exporting Data

1. **Click "Export Data"** on dashboard
2. **Select filters** (optional):
   - Date range
   - Specific schools/districts (if applicable)
3. **CSV file downloads** with all data in your scope

---

### Workflow 3: Tracking Unassessed Students (School & District Coordinators)

#### Step 1: Access Unassessed Students

1. **Click "Unassessed Students"** in navigation menu
2. **You will see**:
   - List of students in your scope who need assessment
   - Filters:
     - Test type (Pre-test, Post-test, Both)
     - School (District Coordinators only)
     - Grade level

#### Step 2: Use the Information

- **Identify** which students need assessment
- **See** which teachers' classes have unassessed students
- **Track** assessment completion progress
- **Export** the list if needed

---

## Quick Reference

### Navigation by Role

#### CLMD Coordinator (Admin)
- Dashboard
- Library Management
- User Management
- Activity Logs
- Profile

#### Teacher
- Dashboard
- Reading Materials
- My Classes
- Assessment Results
- Unassessed Students
- Profile

#### School Coordinator
- Dashboard
- User Management
- Unassessed Students
- Profile

#### District Coordinator
- Dashboard
- User Management
- Unassessed Students
- Profile

#### Division Coordinator
- Dashboard
- User Management
- Profile

---

### Important Rules

✅ **MUST DO**:
- Accept Terms of Service on first login
- Use Grade 11 or 12 only
- Progress reading levels sequentially (Word → Phrase → Sentence → Paragraph)
- Complete assessments in one session

❌ **CANNOT DO**:
- Retake same test type for same student
- Create users at your level (only one level below)
- Upload files larger than 10MB
- Skip reading level progression

---

### Assessment Process Summary

1. **Select Material** → Choose pre-test or post-test material
2. **Select Class & Students** → Choose which students to assess
3. **Reading Phase** → Student reads material (no time limit)
4. **Reading Level** → Teacher evaluates highest level achieved
5. **Questions** → Only if student reached Paragraph Level
6. **Results** → Automatic scoring and classification

---

### Getting Help

**If you need assistance**:
1. Check this manual first
2. Contact your coordinator:
   - Teachers → School Coordinator
   - School Coordinators → District Coordinator
   - District Coordinators → Division Coordinator
   - Division Coordinators → CLMD Coordinator

**When reporting issues**, include:
- Your role
- What you were trying to do
- Error message (if any)
- Steps you took

---

**End of User Manual**

*For system updates and additional support, contact your CLMD Coordinator or system administrator.*
