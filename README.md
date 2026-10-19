# WCS File Manager — ATM Maintenance Desk

A local-only browser application. It runs by opening `index.html`; Python, a web server, an account, and an internet connection are not needed. Records, attachments, and audit history are stored in the current browser profile on this PC.

## Start

1. Open this folder in File Explorer.
2. Double-click `index.html` and choose Chrome or Edge if asked.
3. To sync schedules, choose **Sync schedules from Excel** and select the bank `.xlsx` files. Review the proposed additions, changes, unchanged rows, and missing rows before applying. The workbook contents are read locally in the browser.

This edition supports `.xlsx`, `.xlsm`, `.csv`, and `.tsv` schedule files. The picker also shows older `.xls` files so you can identify them, but those must first be converted in Excel: choose **File → Save As → Excel Workbook (*.xlsx)** and save a separate `.xlsx` copy. Keep the original `.xls` files unchanged. Thereafter, update the `.xlsx` copies in Excel and select the updated files in the app to sync. A browser-only page cannot silently watch the schedule folder; Excel file selection is an explicit user action.

If you previously used the Python-based tracker and made a **Backup data** JSON file, choose **Restore backup** here to migrate its visits and attachments. The offline edition stores its data separately.

## Schedule import behavior

- The importer looks for columns named like Serial/ATM, Branch/Location, and Status across workbook worksheets.
- Bank/year are inferred from the filename (for example, `CAL BANK 2026 NORMAL SCHEDULE.xlsx`). Review the preview and any file errors before applying the sync.
- A matching bank/year/ATM record is updated from the schedule; its engineer, actual work date, notes, signed report, packet, and confirmation fields are preserved. New ATM rows are added. Removed schedule rows remain in the tracker and are marked for review instead of being deleted.
- Schedule status maps `DONE` to Completed, progress/ongoing to In progress, and other values to Not started. The original Excel status is retained for review.
- This browser-only app does not monitor files or sync changes while Excel is open. Save the workbook, then import the updated file again.

## Data safety and security

Use the same PC, browser, and browser profile each time. Do not clear browser data or use private/incognito mode. Use **Backup data** regularly and store the JSON backup in an organization-approved location. The app shows the last recorded download and flags a backup after 14 days; keep the downloaded file in the approved location. **Restore backup** replaces current tracker records after confirmation.

Files are processed locally and are not uploaded to a service. This app does not provide login or multi-user access. Follow your organization's requirements for customer information, device access, backups, and retention.

## Main workflow

1. Sync schedules and review the preview, including missing rows and workbook errors, before applying. **Undo last Excel sync** restores the saved pre-sync visits and audit history; it also replaces edits made after that sync.
2. Open or add the matching visit when the signed engineer report arrives. Record actual engineer/date/work, attach the report, and update its status.
3. Mark packets Ready/Sent and enter customer confirmations as they arrive.
4. Use **Outstanding** to find next actions. The **Packet preflight** view checks engineer assignment, completed work, received report status, and report attachment before you mark/select a packet for printing. The **Intelligence** view provides a local, rule-based risk brief with reasons for each flag and a workload snapshot by engineer; use **Print review brief** to create a paper summary. Customer confirmations pending for seven or more days are marked overdue and sorted to the top. Use filters to prepare packets, and **Print selected** to create engineer-grouped paperwork.
5. Export a CSV or download a backup as needed.

## Limitations

- Old `.xls` files must first be saved as `.xlsx` in Excel. Password-protected files may not import.
- Browser-local data is tied to one browser profile on this PC. It is not a shared team database, and a local HTML file does not grant the browser unattended access to a folder.
- Printed packets show attached images. For a PDF report, the packet has a link to open the named PDF; open and print that PDF separately because browser print views cannot reliably include PDF pages. Review printed output before sending it to a customer.


## GitHub repository

The [WCS File Manager Project Guide](WCS-File-Manager-Project-Guide.docx) covers setup, schedule imports, visit tracking, packet preparation, backups, privacy, and troubleshooting.

This repository should contain only the application source files and project documentation. Do not add customer schedules, signed maintenance reports, exported packets, or tracker backup files. Those stay in browser storage and local backups; they are not part of the app source.


