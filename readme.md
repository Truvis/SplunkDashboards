*be sure to star and follow this project if you like it. By doing so it lets me know which of my works people enjoy the most so development can be prioritized*

# Dashboards
When I started teaching myself Splunk and saw that you could create dashboards, I quickly became addicited and started building out as many ideas as I possibly could. The goal is to figure out how to package these into an app that can be quickly deployed and configured to any splunk instance.

The other part that inspired this was to build out a Threat Hunting envirnment for trying to detect attacks and also learning how to not get noticed when doing red team engagments. 

Be sure to drop ideas and improvements! I'm still learning and would enjoy other's viewpoints!

- *TODO: Add colors across all dashboards*
- *TODO: Standardize naming of fields*
- *TODO: Add summary of what each dashboard does*
- *TODO: List configuration settings and requirements on hosts such as index, sourcetype, source*

## Windows
### Configuration

### Dashboards
#### User Windows Security Overview [MAIN]
![2020_09_22_06_11_24_Truvis_User_Windows_Security_Overview_MAIN_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93869920-7f5a2a00-fc9a-11ea-8aa3-b91faf7f3d0a.png)

#### Host Windows Security Overview [MAIN]
![2020_09_22_06_13_32_Truvis_Host_Windows_Security_Overview_MAIN_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870172-ca743d00-fc9a-11ea-943e-1483ada2b8b8.png)

## Linux
### Configuration
- Uses a custom history configuration on the host machines
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Linux_History

### Dashboards
#### User Linux Security Overview [MAIN]
![2020_09_22_05_54_26_What_is_Penetration_Testing_Step_By_Step_Process_Methods_Imperva](https://user-images.githubusercontent.com/23244379/93868232-2a1d1900-fc98-11ea-9d05-9d91bd429e0c.png)

#### Host Linux Security Overview [MAIN]
*TODO: Update to use the new linux history TA to get src_ip*
![2020_09_22_06_06_47_What_is_Penetration_Testing_Step_By_Step_Process_Methods_Imperva](https://user-images.githubusercontent.com/23244379/93869508-df9c9c00-fc99-11ea-83d6-17792cb43410.png)

#### Host Linux Dashboard by ENDPOINT [SUB]
*TODO: Still under development and needs to be update to pull from new sources*
![2020_09_22_06_07_52_Truvis_Host_Linux_Dashboard_by_ENDPOINT_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93869580-fc38d400-fc99-11ea-8a0f-157eec74de97.png)


## Suricata
### Configuration
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Suricata5 
- Uses a server configured with port mirror running suricata*

### Dashboards
#### Suricata Network Overview [MAIN]
*TODO: Add the ability to exclude in filter*
![2020_09_22_06_15_56_What_is_Penetration_Testing_Step_By_Step_Process_Methods_Imperva](https://user-images.githubusercontent.com/23244379/93870366-1fb04e80-fc9b-11ea-9ca5-6b66e0cfabde.png)

#### Suricata Host Overview [SUB]
*TODO: Needs HOST input added for host control*
![2020_09_22_06_17_09_Truvis_Suricata_Host_Overview_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870480-4a9aa280-fc9b-11ea-94de-04027dfd9ff7.png)

#### Suricata Categories Overview [SUB]
![2020_09_22_06_18_25_Truvis_Suricata_Categories_Overview_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870605-76b62380-fc9b-11ea-9906-d4f5b311b474.png)

#### Suricata Signature Overview [SUB]
![2020_09_22_06_19_14_Truvis_Suricata_Signature_Overview_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870680-93eaf200-fc9b-11ea-8e6c-e09c58047f92.png)


## Network
### Configuration

### Dashboards
#### Network Intelligence Overview [MAIN]
*TODO: Need threatintel list for refference*
![2020_09_22_06_20_59_Truvis_Network_Intelligence_Overview_MAIN_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870863-d280ac80-fc9b-11ea-8a31-d9d37a479de0.png)

#### Network Intelligence by ENDPOINT [SUB]
*TODO: Need threatintel list for refference*
![2020_09_22_06_22_06_Truvis_Network_Intelligence_by_ENDPOINT_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93870988-fa701000-fc9b-11ea-9671-c21d2a9209ad.png)

#### Blocked Out Going Connections BY IP [MAIN]
![2020_09_22_06_23_31_Truvis_Blocked_Out_Going_Connections_BY_IP_MAIN_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93871130-2be8db80-fc9c-11ea-8f1d-ecce7c70bfd2.png)

#### Blocked Out Going Connections by ENDPOINT [SUB]
*TODO: Needs host control*
![2020_09_22_06_24_54_Truvis_Blocked_Out_Going_Connections_by_ENDPOINT_SUB_Splunk_8 0 5](https://user-images.githubusercontent.com/23244379/93871266-5d61a700-fc9c-11ea-875d-5905d7f472c6.png)


## Threat Hutning
### Configuration
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Suricata5 
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Linux_History
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Opnsense-20.1.X
- Uses PLUGIN https://github.com/Truvis/Splunk_TA_Truvis_Zeek
- Uses a server configured with port mirror running suricata*
- *TODO: Breakout the bigger dashes to subs based on services for example*

### Dashboards
#### Truvis-Threat Intelligence Windows Accounts [MAIN]
![2020-10-17 12_34_22-Truvis-Threat Intelligence Windows Accounts  MAIN  _ Splunk 8 0 5](https://user-images.githubusercontent.com/23244379/96348204-22714a00-1075-11eb-8872-83e50f9b2442.png)

#### Truvis-Threat Intelligence Network [MAIN]
![2020-10-17 12_33_38-root@splunk_~](https://user-images.githubusercontent.com/23244379/96348196-0a012f80-1075-11eb-978f-4ca5fbf37065.png)


