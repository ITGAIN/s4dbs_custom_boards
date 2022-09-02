# Linux Disk Throughput Disk Map
## Requirements
- Version: minimum 1.3.0
- Extra Table for mapping (spg_mon_os.disk_map)

## Shown Data/Information
This board is a copy of the disk throughput board but can be enriched with mapping names for devices. In the filter area at the top the "Use Diskmapping" selector can be set to yes to join in a mapping table. If a device is not within the mapping table it wont get displayed. In addition during mapping an entry can be set to visible=false to be hidden in the charts.

## Mapping Table
### Design and DDL
Design of the table:

| display_name | device | device_display_name | visible |
|--------------|--------|---------------------|---------|
| display name of the host |device name on the host | mapped new name | true or false if should be visble or not |

The mapping table can be created like this:
````SQL
CREATE TABLE spg_mon_os.disk_map (
	display_name varchar NOT NULL,
	device varchar NOT NULL,
	device_display_name varchar NOT NULL,
	visible bool NOT NULL,
	CONSTRAINT disk_map_pk PRIMARY KEY (display_name, device)
);
````

### Populating
Example to populate one mapping:
````SQL
INSERT INTO spg_mon_os.disk_map
(display_name, device, device_display_name, visible)
VALUES('my_prod_linux_host', 'sda1', '/databases', true);
````

Find  missing entries for mapping:
````SQL
select
	display_name, device, ' ' as device_display_name, true as visible
from spg_mon_os.proc_diskstats pd
where
	not exists(
	    select 1 from spg_mon_os.disk_map dm where dm.display_name = pd.display_name and dm.device = pd.device
    )
group by	
    1, 2, 3, 4;
````

Insert all missing mapping entries with default map name (and edit names and visibility afterwards)
````SQL
insert into spg_mon_os.disk_map 
(display_name, device, device_display_name, visible)
(
        select display_name ,device,device,device||' not mapped yet',true 
        from spg_mon_os.proc_diskstats pd 
        where not exists (
            select 1 from spg_mon_os.disk_map dm where dm.display_name=pd.display_name and dm.device=pd.device
        )
        group by 1,2
);
````

