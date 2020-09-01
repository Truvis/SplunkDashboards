# Dashboards
When I started teaching myself Splunk and saw that you could create dashboards, I quickly became addicited and started building out as many ideas as I possibly could. The goal is to figure out how to package these into an app that can be quickly deployed and configured to any splunk instance.

The other part that inspired this was to build out a Threat Hunting envirnment for trying  to detect attacks and also learning how to not get noticed when doing red team engagments. 

Be sure to drop ideas and improvements! I'm still learning and would enjoy other's viewpoints!

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

## Linux Host Dashboard (dashboard 5)
This dashboard was designed to be a drilldown and host overview offering lots of relevant information for the host specifically.
![5](https://user-images.githubusercontent.com/23244379/91901148-d0fc2f80-ec6d-11ea-9ac8-cdf74aaad534.png)

## Linux Command Alerts (dashboard 6)
This dashboard will list executed scripts and known applications and strings that may be used for malicious intent. Clicking an item drills down to  Dashboard 5
![6](https://user-images.githubusercontent.com/23244379/91859967-0cc8d200-ec39-11ea-98cf-4c1eaaf54e4f.png)
