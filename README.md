# SmartThings <-> UniFi Presence Sensor

**Integration for SmartThings to use UniFi wireless clients as presence sensors**
This will allow you to select from a list of known UniFi wireless clients to monitor their presence. By selecting device(s) to monitor, a script will run every 5 seconds to check the UniFi controller's current status of the monitored device(s). If the device can't be seen by any UniFi Access Point, then the device is reported offline. A device is "offline" when it is not connected to an UniFi wireless network.

You can also monitor guest connected to a UniFi hotspot by enabling the guest option.

## Getting Started

These instructions will help you get this solution implemented. I'm going to assume a working local UniFi Controller already exist on the network.

### What are we going to be setting up / installing

Here are the things that we will need to install / configure

- UniFi Bridge (REST API server to facilitate communication between SmartThings and the UniFi Controller)
  - This can be installed from [here](https://github.com/xtreme22886/SmartThings_UniFi-Presence-REST)
- UniFi Wireless Presence (SmartThings SmartApp)
- UniFi Presence Sensor (SmartThings Device Handler)

## Installing SmartApp and Device Handler
**First things first. Get the UniFi Bridge up and running before proceeding**

There are two ways you can install the SmartThings SmartApp and Device Handler.
1. VIA the SmartThings IDE GitHub integration
   - Owner = xtreme22886
   - Name = SmartThings_UniFi-Presence-Sensor
   - Branch = master
2. VIA copying / pasting the code in the SmartThinge IDE
   - SmartApp = unifi-wireless-presence.groovy
   - Device Handler = unifi-presence-sensor.groovy

Instead of describing the two methods of installation here, I'm going to refer you to the documentation for installing the [SmartThings Community Installer](http://thingsthataresmart.wiki/index.php?title=Community_Installer_(Free_Marketplace)) as it's well laid out. You will need to be familiar with "Installation" section, specifically installing from code, installing from GitHub and OAuth setup.

Setup Steps:
1. Install SmartApp
   - Make sure to `Publish` and **enabled** `OAuth` for this app
2. Install Device Handler
   - Make sure to `Publish` this device handler
3. In the **SmartThings Classic** mobile app
   - Automation > SmartApps > Add a SmartApp
   - My Apps > UniFi Wireless Presence
   - Enter in information for **Bridge Address**, **UniFi Controller Address**, **UniFi Controller Username**, **UniFi Controller Password** and **UniFi Controller Site**
4. Click **Save** all the way out of the SmartApp
   
**NOTE:** The **UniFi Controller Site** is **NOT** the *name* of the site but rather the *id* of the site. Take "https://x.x.x.x:8443/manage/site/default/dashboard" as an example; the *site id* is what is listed directly after **/site/**. In this cause, it would be **default**.

After setup has been completed, we can begin to monitor device(s)
1. Go back into the SmartApp
2. Click on **UniFi Client List**
3. Wait 5 seconds for the list of wireless clients to refresh and populate
4. Click on `Tap to select`
5. Select the device(s) you want to monitor
6. Click **Save** all the way out of the SmartApp
7. Go back to your list of *Things* and locate the new presence device that was created
   - Feel free to rename this device as needed
   
**Notes:**
- Anytime you add/remove devices to be monitored, the SmartApp with add/remove the associated *thing*

### Donate
[PayPal.me](https://www.paypal.com/donate?hosted_button_id=HEZ9EPNJR2UYA&source=url)
