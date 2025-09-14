# Windows 11 Upgrade Dashboard – Automation + Power BI

## Overview
This project automates the Windows 11 upgrade reporting process for the MTA.
Every day at 11:45 AM and 4:45 PM, a Power Automate flow refreshes an Excel baseline and triggers Power BI to update.

## How It Works
1. **Power Automate Flow**  
   - Calculates current Monday’s date  
   - Builds dynamic filename (`Managers Dashboard 9.15.25.xlsx`)  
   - Finds the weekly Excel report in SharePoint  
   - Deletes the old file in the target folder  
   - Uploads the new file as `Managers Dashboard.xlsx`  
   - Triggers Power BI dataset refresh  

   ![Flow Screenshot](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/PowerAutomateWin11.png)

2. **Data Sources**
   - SCCM weekly export (serial, device name, IP)
   - Networking IP-to-location mapping
   - MTA Open Data with latitude/longitude
   - Joins handled in Power Query for repeatability

   ![Data Merge Screenshot](screenshots/data_merge.png)

3. **Power BI Dashboard**
   - **Map**: Sites with device counts (bubble size), tooltips with ticket status & device type  
   - **Filters**: Location, device type, ticket status  
   - **Completion Bins**: 0%, 25–49%, 50–74%, etc.  

   ![Dashboard Map Screenshot](screenshots/dashboard.png)

## Future Expansion
- Add mobile assets (Workspace ONE)
- Integrate ServiceNow + WMS
- Unified asset map across all platforms

---

## 3. Repo Structure
Your repo might look like:

