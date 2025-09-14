# Windows 11 Upgrade Dashboard – Automation + Power BI

## Overview
This project automates the Windows 11 upgrade reporting process.
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
   - SCCM weekly export (serial number for asset, device name, IP)
   - Networking IP-to-location mapping (Gives IP addresses the location names)
   - MTA Open Data source in order to get latitude/longitude (now locations have Lat/ Long)
   - Joins handled in Power Query for repeatability

The first page provides a summary of each domain, including the associated RITMs (requested item number) and their corresponding locations. Each item is interactive—clicking on it navigates directly to the relevant detailed page.
   ![Data Merge Screenshot](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/SummaryPage.png)

3. **Power BI Dashboard**
   - **Map**: Sites with device counts (bubble size), tooltips with ticket status & device type  
   - **Filters**: Location, device type, ticket status  
   - **Completion Bins**: 0%, 25–49%, 50–74%, etc.  

   ![Dashboard Map Screenshot]([https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/Win11Dashboard%20Main%20Page.png](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/PercentageCompleteEachLocation.png))


   ![Dashboard Map Percentage for Each Location](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/PercentageCompleteEachLocation.png)
## Future Expansion
- Add mobile assets (Workspace ONE)
- Integrate ServiceNow + WMS
- Unified asset map across all platforms

---



