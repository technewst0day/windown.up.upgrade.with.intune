# windown up upgrade with intune

[![windown up upgrade with intune](gett-stateed.png)](https://github.com/technewst0day/windown.up.upgrade.with.intune)

Over time you have deployed maybe several Win32 apps, but those apps need to be maintained or updated. I want to update a Win32 app based on a new version number. I think this can be done in two ways, deploy a new version of the app by adding another (version) app to the Windows apps or update the Win32 app in its original configuration.

## Deploy Win32 apps with Microsoft Intune

At Microsoft Ignite Brad Anderson announced a new feature for Microsoft Intune; deploy Win32 applications with Microsoft Intune. A much requested feature for Intune, to remove another blocker in modern desktop deployment. In this blog I will have a look at this feature with the deployment of Google Chrome with Intune.

### Pre-requisites

**_There are some pre-requisites for the client and application:_**

* Windows 10 1607 or later and at this moment Enterprise edition
* Client needs to be (Hybrid) Azure AD joined
* Enrolled in Intune
* Application size is capped at 2GB

### Deploy the app with Intune

Now it`s time to upload the file to Intune and deploy it to your Intune managed Windows 10 devices.

* Logon to the Microsoft 365 Device Management portal
* Click on Client Apps, Apps, Add.
* Select Windows app (Win32)
* open the App package file tab and select your .intunewin file to upload to Intune.
* At the App information tab at least fill in a Name for the application, a Description and the Publisher.
* On the Program tab you need to provide the install and uninstall commands. In this case the commands are pre-configured.
* On the Requirements tab for a minimum you need to choose Operating system architecture and the Minimum operating system.
* On the Detection rules tab you are able to define a detection rule. Choose Manually configure detection rules and as rule type MSI. If not already pre-configured, fill in the MSI product code. Other rule types are file and registry. If needed you can add multiple rules or use a detection script.
* On the last tab (Return codes) verify the pre-configured codes, click OK and Add app to start uploading the application.

## Manage Google Update settings with Microsoft Intune

This is a follow-up post on Managing Google Chrome settings with Microsoft Intune. In this post I will show how we can use Microsoft Endpoint Manager (Intune) to manage Google Update settings.

Like the Google Chrome settings, the Google Update settings can also be managed using a custom configuration profile for Windows 10. The policy consists of two parts. The first part is used to deploy the Google Update ADMX file to the Intune managed device. The second part of the policy is used to manage the settings of choice.
