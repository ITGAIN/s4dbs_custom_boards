# s4dbs_custom_boards
This repository stores custom dashboards for the monitoring solution speedgain for databases (speedgain.com)

This Boards can be imported / provisioned to a Grafana that is connected to a Speedgain for Databases Repository via mounting/copy files or folder to /s4dbs_custom/boards inside the grafana container. 

All dashboards seen here are subject to be integrated into the tooling itself once in a while (only with permission of the owner). 

One folder per area (Db2, PostgreSQL, SQL Server, Oracle, Linux, Windows, Speedgain System) and one folder per dashboard is needed. 

Please provide a readme besides the dashboard describing the prereqs and needed collectors and minimum version of speedgain for databases for that board to be working. Information on every panel of how to understand displayed metrics would be nice to have.
