# Data Storage Setup Guide

The Data Storage tab is the backbone of your tracking system. It stores all interaction records in a single location, allowing for easy querying and filtering.

## Structure

Create a simple tabular structure with these columns:

| Timestamp | Entry Date | Teacher | Student | Status | Update/Notes | Next Steps |
|-----------|------------|---------|---------|--------|--------------|------------|
| [Auto] | 3/1/2025 | Ms. Jones | Alex Smith | Working Actively | Text entry... | Text entry... |

## Setup Instructions

1. **Create the Headers:**
   - A1: "Timestamp" (when the entry was submitted)
   - B1: "Entry Date" (the actual date of the interaction)
   - C1: "Teacher" (who logged the interaction)
   - D1: "Student" (which student was involved)
   - E1: "Status" (current working status)
   - F1: "Update/Notes" (details about the interaction)
   - G1: "Next Steps" (action items for next meeting)

2. **Format the Headers:**
   - Make them bold
   - Add background color
   - Freeze the header row (View > Freeze > 1 row)

3. **Column Formatting:**
   - Timestamp (Column A): Date time format
   - Entry Date (Column B): Date format
   - Status (Column E): Consider using data validation for consistent values
   - Update/Notes & Next Steps (Columns F-G): Wrap text

4. **Test Data:**
   - Add a few sample entries to test your formulas

## Protecting the Data

Since this tab contains all your historical data, it's important to protect it:

1. **Protect the Sheet:**
   - Right-click on the tab > Protect sheet
   - Allow only yourself and necessary collaborators to edit

2. **Hide the Sheet (Optional):**
   - Right-click on the tab > Hide sheet
   - This prevents accidental edits while still allowing the data to be accessed by formulas

## How This Works with Other Tabs

The Data Storage tab is designed to:

1. **Receive new entries** from the Entry Form tab via the submit script
2. **Supply data** to the Dashboard via lookup formulas
3. **Populate individual student tabs** via filtering formulas

## Importing Existing Data

If you have existing notes in another format:

1. Format your current data to match these columns
2. Copy and paste into the Data Storage tab
3. Make sure dates are properly formatted
4. For status, either use "Imported/Historical" or leave blank

## Maintenance Tips

1. **Sorting:**
   - Do not manually sort this sheet, as it could break the dashboard formulas
   - New entries should always be appended at the bottom

2. **Archiving:**
   - For large datasets, consider archiving old entries (older than the current school year)
   - Create an "Archive" tab with the same structure
   - Move older entries there and update your formulas to include both tabs

3. **Backup:**
   - Periodically export this tab as a CSV for backup
   - File > Download > Comma-separated values

4. **Performance:**
   - If the sheet becomes slow, consider limiting your QUERY formulas to specific ranges
   - Replace A:G with A1:G1000 (adjust the number as needed)
