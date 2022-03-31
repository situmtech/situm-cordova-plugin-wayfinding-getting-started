# Cordova SitumWayfinding Plugin Sample App

## Description

This sample app has been designed to allow you test [SitumWayfinding Plugin for Cordova](https://github.com/situmtech/situm-cordova-plugin-wayfinding).

It is a simple app with two buttons:

* The **Add** button allows you to load SitumWayfinding view in screen.
* The **Remove** button removes SitumWayfinding from the screen and stops positioning and routing processes.

Once the SitumWayfinding view is loaded into screen you will be able to:
  1. Load a Situm Map with [the building specified in config.xml](https://github.com/situmtech/situm-cordova-plugin-wayfinding-getting-started/blob/master/config.xml). This building has to be defined in your account.
  2. Start the positioning in the specified building.
  3. Start navigation in the specified building.

Below you can see three screenshots of the example app. [Initial View] shows the app just after launch. If you click on the Add button, SitumWayfinding is loaded into the screen [SitumWayfinding Loaded]. [Navigation] shows the app after requesting a route to one of the building points of interest.  

Initial View               | SitumWayfinding Loaded     | Navigation
:-------------------------:|:-------------------------: |:-------------------------:
![](images/start.png?raw=true "Initial view")  |  ![SitumWayfinding Loaded](images/loaded.png?raw=true "SitumWayfindingLoaded") | ![Navigation](images/navigation.png?raw=true "Navigation")


## Submitting Contributions

You will need to sign a Contributor License Agreement (CLA) before making a submission. 
[Learn more here.](https://situm.com/contributions/)

## Setup your Situm account

In this tutorial, we will guide you step by step to set up your first Cordova application using Cordova Situm Plugin. Before starting to write code, we recommend you to set up an account in our [Dashboard](https://dashboard.situm.es), retrieve your API KEY and configure your first building.

1. Go to the [sign in form](http://dashboard.situm.es/accounts/register) and enter your username and password to sign in.

2. Go to the [account section](https://dashboard.situm.es/accounts/profile) and on the bottom, click on “generate one” to generate your API KEY.

3. Go to the [buildings section](http://dashboard.situm.es/buildings) and create your first building.

4. Download Situm Mapping Tool in Play Store (Only Android devices) and calibrate your building. Check out our user guide for detailed information.

5. You are ready for building your own Cordova applications. Please check next steps about requirements

## Installing pre-requisites

### Configure cordova:

* [Install Cordova CLI](https://cordova.apache.org/docs/en/latest/guide/cli/index.html#installing-the-cordova-cli)
* [Cordova Docs](https://cordova.apache.org/docs/en/latest/guide/overview/index.html)
* [Hello world Cordova example](https://cordova.apache.org/docs/en/latest/guide/cli/index.html#add-platforms)

### Cordova requirements:

* [Android](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#installing-the-requirements)
* [iOS](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/#installing-the-requirements)
* [Cocoapods](https://guides.cocoapods.org/using/getting-started.html) (Only if you need your application to run in iOS devices)

## App configuration(#app-configuration)

Inside the example directory, add your desired platforms with:

    $> cd <PATH_TO_EXAMPLE>/situm-cordova-plugin-wayfinding-getting-started/

    $> cordova platform add ios

    $> cordova platform add android

The plugin will be automatically installed when you add the platforms. If removed at any moment, it can be add again with:

    $> cordova plugin add situm-cordova-plugin-wayfinding

Afterwards, provide the System Permission and API keys defined in [Cordova Plugin Wayfinding](https://github.com/situmtech/situm-cordova-plugin-wayfinding#system-permission).

## Code Explanation

You can take a look to [index.html](https://github.com/situmtech/situm-cordova-plugin-wayfinding-getting-started/blob/master/www/index.html) to see how load and unload methods are invoked.

**Load**: When add button is clicked, load SitumWayfinding view in map_div.

```javascript

      let librarySettings = {
          'dashboardUrl': 'https://dashboard.situm.es',
          'hasSearchView': true,
          'searchViewPlaceholder': 'Cordova Wayfinding',
          'useDashboardTheme': false
        };

      var add_button = document.getElementById("add_button");
      add_button.addEventListener("click", function() {
            var map_div = document.getElementById("map_canvas");
            map = plugin.situm.wayfinding.situmWayfindingPlugin.load(map_div, librarySettings, function(success) {},function(error) {});
      });
```

**Unload**: When remove button is clicked, unload the SitumWayfinding view.

```javascript
      var remove_button = document.getElementById("remove_button");
      remove_button.addEventListener("click", function() {
            plugin.situm.wayfinding.situmWayfindingPlugin.unload(map, function(success) {},function(error) {});
      });
```

## Limitations

* Using the "Go back" button in iOS will block the module for the user. It will be fixed in coming releases.
* The buttons "Add" and "Remove" should be pressed in that order and only once. Repeated touchs to the same button without pressing the other first will result in unexpected failure.

## License

SitumWayfinding is available under the MIT license. See the LICENSE file for more info.
