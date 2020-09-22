*be sure to star and follow this project if you like it. By doing so it lets me know which of my works people enjoy the most so development can be prioritized*

# Dashboards
When I started teaching myself Splunk and saw that you could create dashboards, I quickly became addicited and started building out as many ideas as I possibly could. The goal is to figure out how to package these into an app that can be quickly deployed and configured to any splunk instance.

The other part that inspired this was to build out a Threat Hunting envirnment for trying to detect attacks and also learning how to not get noticed when doing red team engagments. 

Be sure to drop ideas and improvements! I'm still learning and would enjoy other's viewpoints!

- *TODO: Add colors across all dashboards*
- *TODO: Standardize naming of fields*
- *TODO: Add summary of what each dashboard does*

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

### Dashboards
#### Threat Intelligence [MAIN]






## Blocked Out Going Connections BY IP (dashboard 1)
This dashboard pulls blocked outgoing connections from a firewall source and lists how many connections are going out on which ports to easily get an idea of what machine is trying to out on what port and how many times. Clicking on the dashboard opens up Dashboard 2
![1](https://user-images.githubusercontent.com/23244379/91845802-d040aa80-ec27-11ea-8eab-228b5d6a4f45.png)

## Blocked Out Going Connections FROM IP BY port (dashboard 2)
This dashboard is a drilldown from dashboard 1. This is host specific allowing you to see the IPs and port that are being reached out too. It also has quick access to the raw event logs.
![2](https://user-images.githubusercontent.com/23244379/91848469-b6ec2e00-ec28-11ea-809c-f88a5284f434.png)

## Windows Login (dashboard 3)
This dashboard monitors and checks for all logins in a Windows envirnment.
![3](https://user-images.githubusercontent.com/23244379/91849271-cae45f80-ec29-11ea-90f6-fea537dc50a3.png)

## Windows Security Dashboard (dashboard 4)
This dashboard will list out all all relevant Windows Security Events in a quick way to view. 

*TODO: Create a new dashboard for specific ALERTS and add drilldowns to a host based dashboard.*
![4](https://user-images.githubusercontent.com/23244379/91849540-3f1f0300-ec2a-11ea-93b2-f6db1a8f2268.png)

## Host Linux Dashboard by ENDPOINT [SUB] (dashboard 5)
This dashboard was designed to be a drilldown and host overview offering lots of relevant information for the host specifically.
![5](https://user-images.githubusercontent.com/23244379/91901148-d0fc2f80-ec6d-11ea-9ac8-cdf74aaad534.png)

## Host Linux Security Overview [MAIN] (dashboard 6)
This dashboard will list executed scripts and known applications and strings that may be used for malicious intent. Clicking an item drills down to  Dashboard 5
![6](https://user-images.githubusercontent.com/23244379/91859967-0cc8d200-ec39-11ea-98cf-4c1eaaf54e4f.png)

## Suricata Entire Network Overview (dashboard 7)
This dashbard gives a broad overview of the network traffic and possible threats on it. Each item is clickable and drops you down into more in-depth panels.

*REQUIRES: PLUGIN:: https://github.com/Truvis/Splunk_TA_Truvis_Suricata5 -- SERVER:: configured with port mirror running suricata*
![7](https://user-images.githubusercontent.com/23244379/92200224-4c650900-ee47-11ea-91a2-38934aea1de7.png)

## User Linux Security Overview [MAIN] (dashboard 8)
Overview of all Linux User activity
![2020_09_22_05_54_26_What_is_Penetration_Testing_Step_By_Step_Process_Methods_Imperva](https://user-images.githubusercontent.com/23244379/93868232-2a1d1900-fc98-11ea-9d05-9d91bd429e0c.png)

