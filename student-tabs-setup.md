# Student Tabs Setup Guide

Individual student tabs provide a focused view of each student's interaction history. These tabs make it easy to review a specific student's progress and all previous interactions.

## Structure

Each student tab should follow this layout:

### Header Section
Basic student information at the top:
- Name
- Project Focus
- Link to Work
- Any other relevant details

### Interaction Log Section
A chronological list of all interactions with this student:

| Date | Teacher | Status | Update/Notes | Next Steps |
|------|---------|--------|--------------|------------|
| 3/1/2025 | Ms. Jones | Working Actively | Text entry... | Text entry... |
| 2/25/2025 | Mr. Smith | Needs Support | Text entry... | Text entry... |

## Creating Student Tabs

1. **Create a Tab for Each Student:**
   - Name each tab with the student's name
   - Consider a naming convention like "S-FirstnameLastname"

2. **Set Up the Header Section:**
   - Rows 1-5: Basic student information
   - Row 1: Student's full name (large, bold)
   - Row 2: Project focus
   - Row 3: Link to work
   - Row 4: Blank spacer row
   - Row 5: Section title "Interaction Log"

3. **Create the Log Table Headers:**
   - Row 6: Column headers matching the format above
   - Make them bold and add background color
   - Freeze the headers (View > Freeze > 6 rows)

4. **Add the Query Formula:**
   - In cell A7, add this array formula:

```
=QUERY('Data Storage'!A:G, "SELECT B, C, E, F, G WHERE D = '"&A1&"' ORDER BY B DESC", 1)
```

This formula:
- Pulls all entries for this specific student from the Data Storage tab
- Selects only the relevant columns (Date, Teacher, Status, Notes, Next Steps)
- Orders them by date, newest first
- The `1` parameter tells it to skip the header row from Data Storage

## Making It Work

For the formula to work correctly:

1. **Cell A1 Must Contain the Student's Name:**
   - Make sure cell A1 contains exactly the same name as used in the Data Storage tab
   - If you're using "FirstName LastName" in Data Storage, use the same format here

2. **Format the Results:**
   - Apply "Wrap text" to columns for Notes and Next Steps
   - Consider conditional formatting for the Status column

## Enhancements

1. **Add a Summary Section:**
   - Above the log, add a summary of recent activity
   - Use formulas to count interactions, average engagement, etc.

2. **Add Filtering Controls:**
   - Add filter buttons to show only certain types of interactions
   - Use Data > Create a filter

3. **Add a Print View:**
   - Create a button that prepares the tab for printing
   - Hide certain columns, adjust widths, etc.

## Template Approach

To save time when creating new student tabs:

1. **Create a Template Tab:**
   - Set up one perfect student tab with all formulas and formatting
   - Name it "TEMPLATE-Student"

2. **Duplicate for New Students:**
   - Right-click > Duplicate
   - Rename with the student's name
   - Change the value in cell A1 to match the student's name
   - All formulas will update automatically

## Tips

1. **URL Linking:**
   - Use the tab name in URLs to create direct links to specific student tabs
   - Format: `https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit#gid=TAB_ID`

2. **Tab Color Coding:**
   - Consider color-coding tabs by grade level, project type, or other categories
   - Right-click tab > Change color

3. **Keyboard Navigation:**
   - Use Alt+Shift+Down Arrow to quickly insert a new entry at the top of the log

4. **Troubleshooting:**
   - If the QUERY formula returns no results, check that the name in A1 exactly matches what's in Data Storage
   - If the formula displays an error, verify the column references still match Data Storage
