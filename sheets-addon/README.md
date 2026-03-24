# Document Merge Sheets Editor Add-on

This folder contains the separate Editor add-on version of Document Merge for Google Sheets.

It is different from the spreadsheet-bound version in `sheets-extension`:

- `sheets-extension` is installed separately inside each spreadsheet.
- `sheets-addon` is intended to be developed and tested as a Google Sheets Editor add-on from a standalone Apps Script project.

## Files

- `Code.gs`: Sheets Editor add-on entry points, sidebar launcher, merge logic, PDF generation, and email delivery
- `Index.html`: the main HTML sidebar UI
- `EmailEditor.html`: centered rich email editor modal
- `appsscript.json`: manifest and required scopes

## What This Version Does

- Adds a `Document Merge` add-on menu inside Google Sheets
- Opens the same sidebar workflow from the add-on menu
- Supports Google Docs and Google Slides templates
- Generates PDFs, stores them in Drive, and emails them

## How To Set It Up

1. Create a new standalone Apps Script project at `script.google.com`.
2. Copy the files from this folder into that project.
3. Save the project.
4. Open a Google Sheet.
5. In the Apps Script editor, use the Editor add-on test flow to test the project against that sheet.
6. Reload the sheet.
7. Open `Extensions` and look for `Document Merge`.

## Important Notes

- This version should stay in its own standalone Apps Script project.
- It should not replace the spreadsheet-bound version in `sheets-extension`.
- The add-on uses editor-style menus and sidebars, not Workspace homepage cards.
- The first successful test install should ask for authorization because it needs Sheets, Drive, Docs, Slides, triggers, and mail permissions.

## Suggested Test

1. Open the standalone Apps Script project.
2. Use the Editor add-on test flow with a real Google Sheet.
3. Reload that sheet.
4. Open `Extensions -> Document Merge`.
5. Launch the sidebar, connect a template, save the configuration, and run a selected row.
