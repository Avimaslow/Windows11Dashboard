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

   ![Dashboard Map Screenshot](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/Win11Dashboard%20Main%20Page.png)


   ![Dashboard Map Percentage for Each Location](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/PercentageCompleteEachLocation.png)

## Stakeholder Dashboard

This page provides a high-level view of Windows 11 upgrade progress across the organization.  
It is designed to give stakeholders an immediate understanding of overall performance, completion rates, and key areas of focus.

### Top Metrics
- **Number of Assets** – Total devices in scope for upgrade  
- **Closed RITMs** – Number of upgrade requests successfully completed  
- **% Complete** – Overall progress percentage based on total assets  
- **Weekly Closed** – Devices upgraded within the current week  

### Breakdowns & Drill-Downs
- **Top Ten Locations** – Highlights sites with the most remaining open RITMs, showing where attention is needed  
- **Closed by Quarter/Month/Week** – Breakdowns by timeframe and device type (desktop, laptop, monitor)  
- **Closed RITMs by Technician** – Identifies which teams or individuals are closing the most tickets  
- **Domain Summary** – Aggregates upgrades by business domain (e.g., Transit, Metro-North, LIRR)  
- **Status Overview** – Shows closed versus in-progress work, providing transparency into pipeline health  
- **Exclusions** – Lists assets outside upgrade scope (e.g., specialized systems)  

### Interactive Map
- Each bubble represents a location, with size corresponding to the number of assets  
- Stakeholders can identify hotspots, track completion percentages, and explore regions interactively  

### Filters & Search
- Filter by location, device type, or completion percentage  
- Search by RITM or serial number to drill into specific devices  

 ![Stakeholder Page](https://github.com/Avimaslow/Windows11Dashboard/blob/main/screenshots/StakeholdersPage1.png)



## Future Expansion
- Add mobile assets (Workspace ONE)
- Integrate ServiceNow + WMS
- Unified asset map across all platforms

---



