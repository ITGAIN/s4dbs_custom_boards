# Linux Workload Database CPU Distribution
## Requirements
- Version: minimum 1.3.0

## Shown Data/Information
This board is a copy of the linux workload dashboard and has additional panels to show cpu distribution of all databases that are monitored on this host (Db2 and SQL Server).

Display names in the tables are links to the detail boards of the corresponding RDBMS type and specific database/instance. Series in the trendcharts are clickable as well.

Basis to show databases/instances of the selected host is the configured node in the speedgain configuration - not the physical hostname (as Speegain does not have this information when it is collecting Linux metrics). If this host is serving a Db2 database consider using the 'Db2 - System Resources CPU Share' dashboard as that can show the share based on logical and physical hostname - but only for Db2.

## Screenshot
![cpu_share_screenshot](https://github.com/ITGAIN/s4dbs_custom_boards/blob/297ccd60c0024be3b0b0bb0986593bc589206e0c/Linux/Workload%20-%20Database%20CPU%20Distribution/s4dbs_linux_workload_db_cpu_distribution.png?raw=true)
