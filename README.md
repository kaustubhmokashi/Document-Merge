# Document Merge for Google Sheets

This Apps Script project turns a Google Sheet into a sidebar-based PDF automation flow.

## Supported Workflow

1. User opens the extension from a Google Sheet.
2. User connects the sheet to a Google Docs template.
3. The sidebar shows all detected template tags and active-sheet headers.
4. User confirms or changes the suggested mappings.
5. User chooses a trigger:
   - for each new Google Form submission
   - time based: hourly, daily, or weekly
6. User sets who should receive the email.
7. User writes the email subject and body.
8. User chooses the Drive folder where generated PDFs should be stored.
9. On trigger, the script replaces the template placeholders with row values.
10. A PDF is generated and saved to Drive.
11. The PDF is emailed as an attachment.

## Files

- `Code.gs`: sidebar launcher, saved config, trigger setup, PDF generation, email sending, and processing log
- `Index.html`: sidebar UI for the full setup flow
- `appsscript.json`: manifest and required scopes

## How It Works

- The active sheet tab is treated as the response sheet.
- Template placeholders must be written as `{{Tag Name}}`.
- Configuration is saved per spreadsheet in Apps Script user properties.
- A hidden sheet named `_DocumentMergeLog` tracks successful runs so time-based triggers do not regenerate the same row again.
- Manual test buttons let you run the active row or latest unprocessed row immediately.

## Setup

1. Open the destination Google Sheet.
2. Open `Extensions` -> `Apps Script`.
3. Replace the project files with the contents of this folder.
4. Save the project.
5. Reload the spreadsheet.
6. Open the new `Document Merge` menu and choose `Open sidebar`.
7. Save the configuration once so Apps Script can request the needed permissions.

## Required Permissions

- Google Docs access for reading and copying the template
- Google Drive access for storing PDFs
- Google Sheets access for reading response rows and creating the hidden log sheet
- Script trigger access for installable form/time triggers
- Mail access for sending the generated PDF

## Notes

- The template must be a Google Doc, not a PDF.
- The storage location must be a Google Drive folder URL.
- Email fields can include placeholders from the sheet, for example `{{Email}}` or `{{Name}}`.
- The file name pattern also supports placeholders plus `{{rowNumber}}`.
- Form-submit triggers work best when the active sheet is the form response tab.

## Suggested Test

1. Save the sidebar configuration.
2. Select a filled response row.
3. Click `Save + Run Active Row`.
4. Confirm the PDF appears in the chosen Drive folder and arrives in email.
