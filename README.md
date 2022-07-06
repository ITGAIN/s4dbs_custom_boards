# s4dbs_custom_boards
This repository stores custom dashboards for the monitoring solution speedgain for databases (speedgain.com)

This boards can be imported / provisioned to a Grafana that is connected to a Speedgain for Databases Repository via mounting/copy files or folder to /s4dbs_custom/boards inside the grafana container (S4DBs >= V1.3.0). 

All dashboards seen here are subject to be integrated into the tooling itself once in a while (only with permission of the owner). 

One folder per area (Db2, PostgreSQL, SQL Server, Oracle, Linux, Windows, Speedgain System, Overlapping) and one folder per dashboard is needed. 

Do not change given dashboard uid from grafana.

Please provide a readme besides the dashboard describing the prereqs and needed collectors and minimum version of speedgain for databases for that board to be working. Information on every panel of how to understand displayed metrics would be nice to have.

Dashboard tags are used to show them in the menu and alerts in corresponding panels.
Following rules apply:
- overview -> dashboard will be listed in Overview Dashboards
- db2 + visible -> dashboards will be listed in Db2 Dashbaords
- os + visible -> dashboards will be listed in OS Dashboards 
- pg + visible -> dashboards will be listed in PostgreSQL Dashboards
- sqlserver + visible -> dashboards will be listed in SQL Server Dashboards
- alert + custom -> alerts on this dashboards will be shown on S4DBs Overview in S4DBs Custom Alerts Box

Do always specifiy custom tag on custom boards.
