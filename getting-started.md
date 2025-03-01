# Getting Started Guide

This guide will help you set up the Student Progress Tracker from scratch and import your existing data.

## Initial Setup Steps

1. **Create a New Google Sheet**
   - Go to [Google Sheets](https://sheets.google.com)
   - Click on "Blank" to create a new spreadsheet
   - Rename it to "Student Progress Tracker"

2. **Create the Required Tabs**
   - Rename "Sheet1" to "Dashboard"
   - Add these tabs:
     - Entry Form
     - Data Storage
     - One tab per student (e.g., "Alex Smith", "Jamie Wong", etc.)

3. **Set Up Each Component**
   Follow the detailed guides for each component:
   - [Dashboard Setup](dashboard-setup.md)
   - [Entry Form Setup](entry-form-setup.md)
   - [Data Storage Setup](data-storage-setup.md)
   - [Student Tabs Setup](student-tabs-setup.md)

## Importing Existing Data

If you already have notes in a Google Doc or another format:

1. **Prepare Your Existing Data**
   - Organize your current notes by student
   - Identify dates of interactions
   - Determine what would be considered "Status" for each entry
   - Extract any "Next Steps" mentioned

2. **Format for Import**
   - Create a temporary spreadsheet with these columns:
     - Entry Date
     - Teacher
     - Student
     - Status (leave blank if unknown)
     - Update/Notes
     - Next Steps (leave blank if not specified)

3. **Import Process**
   - Copy and paste your formatted data into the Data Storage tab
   - Make sure the Student names match exactly what you'll use in your Dashboard
   - For historical entries without clear status, you can:
     - Leave the Status field blank
     - Use "Imported/Historical"
     - Make your best guess based on the notes

## Sample Data

Here's an example of how to format your existing data for import:

| Entry Date | Teacher | Student | Status | Update/Notes | Next Steps |
|------------|---------|---------|--------|--------------|------------|
| 2/15/2025 | Ms. Jones | Alex Smith | | Student seemed interested in robotics. We discussed potential project ideas related to automated plant watering systems. | Research soil moisture sensors |
| 2/22/2025 | Mr. Brown | Alex Smith | | Alex brought in initial sketches of the watering system design. We discussed power requirements and microcontroller options. | Finalize design and create parts list |
| 2/10/2025 | Ms. Jones | Jamie Wong | | Jamie expressed interest in creative writing. Specifically interested in science fiction. | Provide examples of short sci-fi stories with strong character development |
| 2/20/2025 | Mr. Brown | Jamie Wong | | Jamie hasn't made progress on writing. Spent most of class time browsing unrelated websites. | Schedule one-on-one meeting to discuss barriers |

## Setting Up Your First Student

Let's walk through setting up one complete student entry:

1. **Dashboard Entry:**
   - Add student name: "Alex Smith"
   - Project focus: "Automated Plant Watering System"
   - Link to work: =HYPERLINK("https://docs.google.com/document/d/DOCID", "Alex's Design Doc")

2. **Student Tab Setup:**
   - Create tab named "Alex Smith"
   - Add student name in cell A1
   - Set up header area with project info
   - Add the QUERY formula to pull data from Data Storage

3. **First Entry:**
   - Go to Entry Form
   - Select "Alex Smith" from the dropdown
   - Set date to today
   - Select your name as Teacher
   - Choose a Status (e.g., "Working Actively")
   - Add detailed notes about today's interaction
   - Specify next steps
   - Click Submit

4. **Verify Everything Works:**
   - Check that the entry appears in Data Storage
   - Verify it shows up in Alex's student tab
   - Confirm the Dashboard updates with the latest status and next steps

## Advanced Setup (Optional)

Once you have the basic system working, consider these enhancements:

1. **Custom Menu:**
   Add a custom menu to your spreadsheet for common actions:
   - Tools > Script editor
   - Create a custom menu with functions like:
     - Jump to Entry Form
     - Filter Dashboard by Status
     - Generate Reports

2. **Mobile-Friendly Setup:**
   Make the form easier to use on mobile devices:
   - Increase font sizes on the Entry Form
   - Add extra padding around input fields
   - Test on your phone to ensure usability

3. **Email Notifications:**
   Set up automatic emails when certain events occur:
   - When a student has no interactions for X days
   - When a student's status changes to "Needs Support"
   - Weekly summaries of all interactions

## Getting Help

If you encounter issues with formulas or scripts, check:
- Make sure sheet names match exactly in all formulas
- Verify that student names are consistent across all tabs
- Check that date formats are consistent

For more complex Google Sheets help, the [Google Sheets Help Center](https://support.google.com/docs/topic/9054603) is an excellent resource.
