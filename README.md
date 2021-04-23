# Cordova WearOS Plugin

This plugin enable your Cordova and PhoneGap mobile applications to use the WearOS API.

Platforms:

 * Android 9

Available functionality:

* Subscribe to receive JSONObject messages on a mobile phone from a wearOS connected wearable.
* Send JSONObject messages from a mobile phone to it's wearOS connected wearable.

## Download

Clone the repo into the same directory as your cordova project.

## Installation

Install using the Apache Cordova command line:

    cordova plugin add ../cordova-plugin-wearos

## Future Updates

* Add the ability to have multiple listeners, one for each 
* Include googleFitApi.

## Quick Guide

### Subscibe to Messages

Use function `wearOS.subscribe` to subscribe to messages:

    wearOS.subscribe(success, error)

Adds a Wearable Listener to the Wearable Message Client. All messages and errors are reported to the supplied callback functions. 

Parameters:

    @param {scanCallback} onDeviceFound - Success callback, called repeatedly
    for each message recieved.
    @param {failCallback} onScanError - Error callback.
   

Examples:

    // Scan for all services.
    wearOS.subscribe(
        function(message)
        {
            console.log('message recieved from wearable: ' + message);
        },
        function(errorCode)
        {
            console.log('message recieve error: ' + errorCode);
        }
    );



