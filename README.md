# Cordova WearOS Plugin

This plugin enables your Cordova and PhoneGap mobile applications to use the Google Play Services 17.0.0 Wearable API.

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

* Add the ability to have multiple listeners (data/message/channel).
* Include Google Fit Api.
* Include example wearable code.

## Quick Guide

### Subscibe to Messages

Use function `wearOS.subscribe` to subscribe to messages:

    wearOS.subscribe(success, error)

Subscribe to receive JSONObject messages on a mobile phone from a wearOS connected wearable. This function adds a Wearable Listener to the Wearable Message Client and reports all recievedmessages and errors to the supplied callback functions. 

Parameters:

    @param {successCallback} success - Success callback, called repeatedly
    for each message recieved.
    @param {failCallback} error - Error callback.
   

Examples:

    // Subscribe to  wearable messages
    wearOS.subscribe(
        function(message)
        {
            console.log('message recieved from wearable: ' + message.message);
        },
        function(errorCode)
        {
            console.log('message recieve error: ' + errorCode);
        }
    );


### Send Messages

Use function `wearOS.sendMessage` to subscribe to messages:

    wearOS.sendMessage(jsonObject, messagePath, success, error)

Send JSONObject messages from a mobile phone to it's wearOS connected wearable. This function reports all successes and errors to the supplied callback functions. 

Parameters:

    @param {JSONObject} jsonObject - JSON Object message
    @param {String} messagePath - Path to wear the message will be stored by the wearable.
    @param {successCallback} success - Success callback, called when a message is sent successfully.
    @param {failCallback} error - Error callback.
   

Examples:
    
    var message = {
                    "message" : "hello wearable!",
                    "timestamp" : Date.now()
                  };
                  
    var messagePath = "/messages";
                  
    // Send a message to the connected wearable
    wearOS.sendMessage(
        message,
        messagePath,
        function(message)
        {
            console.log('message sent to wearable: ' + message);
        },
        function(errorCode)
        {
            console.log('message sent error: ' + errorCode);
        }
    );

