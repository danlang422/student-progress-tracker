# Dashboard Setup Guide

The dashboard is the central hub of your student progress tracker, providing an at-a-glance view of all students' current status.

## Dashboard Layout

Your dashboard should follow this structure:

| Student Name | Project Focus | Link to Work | Current Status | Latest Update | Next Steps | Last Updated |
|-------------|--------------|-------------|---------------|--------------|-----------|-------------|
| Alex Smith | Robotics | [Link] | Working Actively | Making progress on circuit design | Test power supply | 2/27/2025 |
| Jamie Wong | Creative Writing | [Link] | Needs Support | Struggling with character development | Provide examples | 2/28/2025 |
| Taylor Johnson | Game Design | [Link] | Disengaged-Passive | No progress since last week | Try different approach | 2/26/2025 |

## Setting Up the Dashboard Tab

1. **Create Headers:** 
   Set up column headers as shown above.

2. **Student Information:**
   - Column A: Student names (manual entry)
   - Column B: Project focus (manual entry)
   - Column C: Links to student work (manual entry, use =HYPERLINK() function)

3. **Dynamic Status Fields:**
   These will update automatically based on the latest entry for each student.

### Formulas for Dynamic Fields

Assuming student names are in column A, use these formulas:

**Current Status (Column D):**
```
=IFERROR(QUERY('Data Storage'!A:G, "SELECT E WHERE D = '"&A2&"' ORDER BY B DESC LIMIT 1"), "No Status")
```

**Latest Update (Column E):**
```
=IFERROR(QUERY('Data Storage'!A:G, "SELECT F WHERE D = '"&A2&"' ORDER BY B DESC LIMIT 1"), "No Updates")
```

**Next Steps (Column F):**
```
=IFERROR(QUERY('Data Storage'!A:G, "SELECT G WHERE D = '"&A2&"' ORDER BY B DESC LIMIT 1"), "No Next Steps")
```

**Last Updated (Column G):**
```
=IFERROR(QUERY('Data Storage'!A:G, "SELECT B WHERE D = '"&A2&"' ORDER BY B DESC LIMIT 1"), "No Entries")
```

## Conditional Formatting (Optional)

Add visual cues based on student status:
1. Select the Status column (Column D)
2. Go to Format > Conditional formatting
3. Add rules:
   - "Working Actively" = Light green
   - "Needs Support" = Light yellow
   - "Disengaged-Passive" = Light orange
   - "Disengaged-Refusing" = Light red
   - "Absent" = Light gray

## Tips

1. **Freezing Headers:**
   Select Row 1, then View > Freeze > 1 row

2. **Filtering:**
   Enable filters on your header row to quickly sort/filter students

3. **Dashboard Sort:**
   Consider adding a button to sort by last updated or status

4. **Protecting Static Cells:**
   You can protect columns A-C to prevent accidental modification of the basic student information
