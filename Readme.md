# Cordova SitumWayfinding Plugin Sample App

## Description

This sample app has been designed to allow you test [SitumWayfinding Plugin for Cordova](https://github.com/mapsplugin/cordova-plugin-situmwayfinding).

It is a simple app with two buttons:

* The **Add** button allows you to load SitumWayfinding view in screen.
* The **Remove** button removes SitumWayfinding from the screen and stops positioning and routing processes.

Once the SitumWayfinding view is loaded into screen you will be able to:
  1. Load a Situm Map with [the building specified in config.xml](#app-configuration). This building has to be defined in your account.
  2. Start the positioning in the specified building.
  3. Start navigation in the specified building.

Below you can see three screenshots of the example app. [Initial View] shows the app just after launch. If you click on the Add button, SitumWayfinding is loaded into the screen [SitumWayfinding Loaded]. [Navigation] shows the app after requesting a route to one of the building points of interest.  

Initial View               | SitumWayfinding Loaded     | Navigation
:-------------------------:|:-------------------------: |:-------------------------:
![](images/start.png?raw=true "Initial view")  |  ![SitumWayfinding Loaded](images/loaded.png?raw=true "SitumWayfindingLoaded") | ![Navigation](images/navigation.png?raw=true "Navigation")



## Installing pre-requisites

### Configure cordova:

* https://cordova.apache.org/docs/en/latest/guide/cli/index.html#installing-the-cordova-cli

### Cordova requirements:

* [Android](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#installing-the-requirements)
* [iOS](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#installing-the-requirements)
* [Cocoapods](https://cocoapods.org/) (Only if you need your application to run in iOS devices)

## App configuration(#app-configuration)

Add your desired platforms with:

    $> cordova platform add ios

    $> cordova platform add android

The plugin will be automatically installed.

Afterwards, provide the System Permission and API keys defined in [Cordova Plugin Wayfinding]().

## Code Explanation

You can take a look to [index.html]() to see how load and unload methods are invoked.

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
* The methods load and unload should be called in that order and only once. Multiple calls to the same method without calling the other first will result in unexpected failure.

## License

SitumWayfinding is available under the MIT license. See the LICENSE file for more info.
