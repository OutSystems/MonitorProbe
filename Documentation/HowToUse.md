


# How to access to Monitor Probe REST API endpoints Documentation

1. Open application as any other OutSystems application and it will allow you to jump to where the application documentation is;
2. Or go to directly to the following URL: _https://&lt;Your Environment URL>/MonitorProbe_

Change the part **&lt;Your Environment URL>** for the url of the environment where you have installed _MonitorProbe_ and the Platform will redirect you to the MonitorProbe main page which the URL will be:
_https://&lt;Your Environment URL>/MonitorProbe/rest/PlatformLogs/_


**On this Monitor Probe main page** you will be able to see:
* The several endpoints from which it is possible to extract monitoring data;
  Each endpoint corresponds to a OutSystems Monitoring data type (Error logs, General logs, etc)  
* And if you expand it you will be able to see  REST API endpoints examples on how to do it.


# How to use Monitor Probe (OutSystems configurations you need to assure)
1. Go to LifeTime and create a service account to access LifetimeAPI methods (applicable if the lifetime version is 11.5 or higher)
![ServiceAccountConfig](https://github.com/OutSystems/MonitorProbe/blob/main/Documentation/images/CreateServiceAccount.png)
2. Save the token of the service account created previously
3. Create an IT user with a default role that has the minimum permission level to access the logs
![Create_IT_User](CreateITUser.png)
4. Install/Update the MonitorProbe
5. Now go to the detail of the module in service center and open the tab site properties
![ModuleDetail](ServiceCenterSitePropertiesDetail.png)
6. Set the effective value of the site property **Authentication_ServiceAccountToken** with the token that you saved on step 3
7. Set the effective value of the site property **MinimumPermissionLevelLabel** with the permission label that the default role has on the environment where you have installed the MonitorProbe
![RoleConfiguration](RoleConfiguration.png)
8. Set the effective value of the site property **TimeToForceAuthentication** with the number of minutes that represent the period of time since the first access until you want to force a new check of user authorization level




## Site properties
* Authentication_ServiceAccountToken
Token of the service account created to access LifeTimeAPI.
* EnforceLifetimeAccessControl
Flag to turn ON/OFF the check the permission level of the user role using LifetimeAPI. Default: _True_
* MinimumPermissionLevelLabel
Label of the minimum permission to access the platform logs. Default: _"Monitor and Add Dependencies"_
* TimeToForceAuthentication
Number of minutes of a "live session" until the system forces a new authentication. Default: _60_


## Timers
* ClearOldAccessControls
Timer to clear old access control records. By default it is set to run weekly on Saturday at 11PM UTC.
