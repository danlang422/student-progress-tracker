# Student Progress Tracker

This repository contains instructions and templates for creating a Google Sheets-based student progress tracking system. This system is designed for teachers who need to coordinate across different locations and maintain detailed logs of student interactions and progress.

## Overview

The tracker consists of several key components:
1. **Main Dashboard** - Overview of all students with their current status
2. **Entry Form** - For adding new interaction logs
3. **Individual Student Tabs** - Detailed history for each student
4. **Data Storage** - Backend sheet for storing all interactions

## Setup Instructions

### 1. Create a New Google Sheet

Start by creating a new Google Sheet with the following tabs:
- Dashboard
- Entry Form
- Data Storage
- Student tabs (one per student)

### 2. Set Up the Data Storage Tab

This is where all entries will be stored.

1. Create columns with the following headers:
   - Timestamp
   - Entry Date
   - Teacher
   - Student
   - Status
   - Update Notes
   - Next Steps

![Data Storage Structure](images/data_storage.png)

### 3. Set Up the Entry Form

Create a user-friendly form for adding new entries:

1. In the Entry Form tab, create a form-like layout:
   ```
   STUDENT INTERACTION LOG ENTRY
   
   Student: [Dropdown]
   Date: [Today's date by default, editable]
   Teacher: [Dropdown]
   Current Status: [Dropdown]
   Update/Notes: [Text area]
   Next Steps: [Text area]
   
   [SUBMIT] button
   ```

2. Set up data validation for dropdowns:
   - Student: List of all student names
   - Teacher: List of teacher names
   - Status: Working Actively, Needs Support, Disengaged-Passive, Disengaged-Refusing, Absent, Imported/Historical

3. Create a script button for submitting entries (details in the Implementation section)

![Entry Form](images/entry_form.png)

### 4. Set Up the Dashboard

Create a dashboard with columns:
- Student Name
- Project Focus/Topic
- Link to Student Work
- Current Status
- Latest Update
- Next Steps
- Date of Last Entry

Use formulas to pull the most recent information from the Data Storage tab.

![Dashboard](images/dashboard.png)

### 5. Individual Student Tabs

For each student:
1. Create a tab named with their full name
2. Set up columns matching the log entry fields
3. Use formulas to display all entries for that student in reverse chronological order

![Student Tab](images/student_tab.png)

## Implementation Details

### Dashboard Formulas

For each student row on the dashboard, use these formulas to pull the latest information:

1. **Current Status:**
```
=IFERROR(INDEX(FILTER('Data Storage'!E:E, 'Data Storage'!D:D=A2), 1), "No Status")
```

2. **Latest Update:**
```
=IFERROR(INDEX(FILTER('Data Storage'!F:F, 'Data Storage'!D:D=A2), 1), "No Updates")
```

3. **Next Steps:**
```
=IFERROR(INDEX(FILTER('Data Storage'!G:G, 'Data Storage'!D:D=A2), 1), "No Next Steps")
```

4. **Date of Last Entry:**
```
=IFERROR(INDEX(FILTER('Data Storage'!B:B, 'Data Storage'!D:D=A2), 1), "No Entries")
```

### Entry Form Submission (Google Apps Script)

Create a button that runs this script when clicked:

```javascript
function submitEntry() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet();
  var formSheet = sheet.getSheetByName("Entry Form");
  var dataSheet = sheet.getSheetByName("Data Storage");
  
  // Get values from form
  var student = formSheet.getRange("B3").getValue();
  var date = formSheet.getRange("B4").getValue();
  var teacher = formSheet.getRange("B5").getValue();
  var status = formSheet.getRange("B6").getValue();
  var notes = formSheet.getRange("B7").getValue();
  var nextSteps = formSheet.getRange("B8").getValue();
  
  // Add timestamp
  var timestamp = new Date();
  
  // Append to Data Storage
  dataSheet.appendRow([timestamp, date, teacher, student, status, notes, nextSteps]);
  
  // Clear form (optional)
  formSheet.getRange("B7").setValue("");
  formSheet.getRange("B8").setValue("");
  
  // Show confirmation
  SpreadsheetApp.getUi().alert("Entry submitted successfully!");
}
```

### Student Tab Formulas

For each student tab, use this formula at the top of the log section to display all entries for that student in reverse chronological order:

```
=SORT(FILTER('Data Storage'!B:G, 'Data Storage'!D:D=SUBSTITUTE(CELL("filename", A1), "[", "")), 1, FALSE)
```

## Tips for Use

1. **Adding Historical Entries:**
   - Use the Entry Form but change the date field to the historical date
   - For status, either leave blank or use "Imported/Historical"

2. **Maintenance:**
   - Periodically archive old entries to keep the sheet performing well
   - Consider using Google Sheets' filter views for quick student filtering

3. **Troubleshooting:**
   - If formulas stop working, check that column references still match data storage
   - If scripts stop working, check Google Apps Script permissions
