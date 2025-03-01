# Student Progress Tracker

A comprehensive Google Sheets-based system for tracking student progress across multiple teachers, locations, and time periods. This tracker is designed for teachers who need to coordinate student interactions and maintain detailed logs without frequent in-person contact.

## Overview

The Student Progress Tracker consists of four main components:

1. **Dashboard** - A central overview of all students with their current status, latest updates, and next steps
2. **Entry Form** - A user-friendly interface for logging new student interactions
3. **Individual Student Tabs** - Detailed history pages for each student showing all past interactions
4. **Data Storage** - A backend sheet that stores all interaction data in a structured format

This system allows you to:
- Track interactions with students across multiple teachers
- Document progress (or lack thereof) systematically
- Maintain consistent status indicators
- Link to student work
- Review complete interaction history by student
- Import historical data

## Getting Started

New to the Student Progress Tracker? Start here:

1. [Getting Started Guide](getting-started.md) - Create your tracker and import existing data
2. [Dashboard Setup](dashboard-setup.md) - Set up your main overview page
3. [Entry Form Setup](entry-form-setup.md) - Create the form for logging interactions
4. [Data Storage Setup](data-storage-setup.md) - Configure the data storage backend
5. [Student Tabs Setup](student-tabs-setup.md) - Create individual student history pages

## Features

- **Simple Interface**: Designed to be used by teachers with varying technical skills
- **Centralized History**: All student interactions stored in one place
- **Real-time Updates**: Dashboard automatically displays the latest information
- **Consistent Status Tracking**: Standardized status indicators for all students
- **Historical Data Support**: Import previous interactions easily
- **Minimal Navigation**: Log entries with just a few clicks
- **Mobile-Friendly**: Works on phones and tablets for on-the-go updates

## Status Indicators

The system uses these standard status indicators to track student engagement:

- **Working Actively**: Student is engaged and making progress
- **Needs Support**: Student is stuck or requires teacher intervention
- **Disengaged-Passive**: Student is present but not working (e.g., browsing unrelated content)
- **Disengaged-Refusing**: Student is actively refusing to participate
- **Absent**: Student was not present for the scheduled interaction
- **Imported/Historical**: For imported entries where status is unclear

## Customization Options

The tracker can be customized in several ways:

- Add additional status options
- Modify the dashboard layout to include different metrics
- Create custom views and filters
- Add automatic email notifications
- Generate summary reports
- Integrate with other Google Workspace apps

## Technical Details

The Student Progress Tracker uses:
- Google Sheets as the database and interface
- Google Apps Script for form submission and automation
- QUERY formulas for data filtering and display
- Data validation for consistent entry
- Conditional formatting for visual cues

## Maintenance

For ongoing maintenance:
- Periodically archive older entries to maintain performance
- Verify that all formulas are functioning correctly
- Check that student information remains consistent across tabs
- Back up your data regularly

## Troubleshooting

Common issues and solutions:
- Make sure sheet names exactly match those referenced in formulas
- Verify that student names are consistent across all tabs
- Check that date formats are consistent
- If scripts stop working, check Google Apps Script permissions

## Contributing

Have improvements or suggestions? Feel free to fork this repository and submit pull requests.

## License

This project is available under the MIT License - feel free to use, modify, and distribute as needed for educational purposes.
