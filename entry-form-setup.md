# Entry Form Setup Guide

The Entry Form is where you'll log all student interactions. It's designed to be simple yet capture all necessary information.

## Form Layout

Create a clean form-like layout:

```
STUDENT INTERACTION LOG ENTRY
----------------------------

Student:      [Dropdown Menu]
Date:         [Date Picker]
Teacher:      [Dropdown Menu]
Status:       [Dropdown Menu]
Update/Notes: [Large Text Area]
Next Steps:   [Large Text Area]

[SUBMIT BUTTON]
```

## Step-by-Step Setup

1. **Create the Form Header:**
   - In cell A1, enter "STUDENT INTERACTION LOG ENTRY" 
   - Format it (bold, larger font, background color)
   - Add a divider in row 2

2. **Create Form Labels (Column A):**
   - A3: "Student:"
   - A4: "Date:"
   - A5: "Teacher:"
   - A6: "Status:"
   - A7: "Update/Notes:"
   - A8: "Next Steps:"

3. **Create Input Fields (Column B):**
   - B3: Student dropdown
   - B4: Date field (default to today)
   - B5: Teacher dropdown
   - B6: Status dropdown
   - B7: Update/Notes text area
   - B8: Next Steps text area

4. **Set Up Data Validation:**

   For Student dropdown (cell B3):
   - Select cell B3
   - Data > Data validation
   - Criteria: List from a range
   - Range: Dashboard!A2:A100 (or wherever your student names are stored)

   For Teacher dropdown (cell B5):
   - Create a named range with teacher names
   - Data > Data validation > List from a range
   - Point to your teacher names list

   For Status dropdown (cell B6):
   - Data > Data validation > List of items
   - Items: Working Actively, Needs Support, Disengaged-Passive, Disengaged-Refusing, Absent, Imported/Historical

5. **Create Default Date:**
   - In cell B4, enter formula: `=TODAY()`
   - This will always default to today's date, but can be edited for historical entries

6. **Format Text Areas:**
   - Select cells B7 and B8
   - Increase row heights for these rows (to create text area appearance)
   - Add borders and background color

## Creating the Submit Button and Script

1. **Add a Submit Button:**
   - Insert > Drawing
   - Create a button labeled "SUBMIT"
   - Place below your form
   - Assign the script to this button

2. **Create the Script:**
   - Tools > Script editor
   - Add this code:

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
  
  // Validation
  if(student == "") {
    SpreadsheetApp.getUi().alert("Please select a student!");
    return;
  }
  
  // Add timestamp
  var timestamp = new Date();
  
  // Append to Data Storage
  dataSheet.appendRow([timestamp, date, teacher, student, status, notes, nextSteps]);
  
  // Clear form fields (except student and teacher)
  formSheet.getRange("B4").setValue(new Date()); // Reset to today
  formSheet.getRange("B6").setValue(""); // Clear status
  formSheet.getRange("B7").setValue(""); // Clear notes
  formSheet.getRange("B8").setValue(""); // Clear next steps
  
  // Show confirmation
  SpreadsheetApp.getUi().alert("Entry submitted successfully!");
}
```

3. **Save the Script:**
   - Save the script with a meaningful name
   - Close the script editor
   - Assign this function to your button

## Tips for Using the Form

1. **For Historical Entries:**
   - Simply change the date field to the historical date
   - Select "Imported/Historical" as status or leave it blank

2. **For Quick Access:**
   - Consider bookmarking this specific tab in your browser
   - Create a menu shortcut to this tab

3. **Entry Confirmation:**
   - The script will clear most fields after successful submission
   - You'll see an alert when the entry is successfully added

4. **Troubleshooting:**
   - If the submit button doesn't work, check script permissions
   - Make sure all referenced sheet names match exactly
