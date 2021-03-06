# Tips for mobile automation daily pain

## Basic installation for Android / iOS platforms
* Install Xcode (https://stackoverflow.com/questions/10335747/how-to-download-xcode-dmg-or-xip-file). 
* Install JDK (http://www.oracle.com/technetwork/java/javase/downloads/index.html). JDK placed in **/Library/Java/JavaVirtualMachines** folder.


Terminal commands for tools installation :
* */usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"*
* *brew install node* **or** *sudo npm cache clean -f && sudo npm install -g n && sudo n 9.8.0* (https://nodejs.org/en/download/releases/)

* brew install libimobiledevice --HEAD
* brew install ios-deploy --HEAD
* brew install ideviceinstaller --HEAD
* brew install carthage --HEAD
* npm install -g appium (or ...@specific version)


## Setup Android
* Download SDK from [Android SDK](https://developer.android.com/studio/index.html).
* Run the *android* tool (included in the SDK/tools folder) and make sure an API Level 17 or greater SDK platform, Google Driver, SDK Tools and SDK platform-tools are installed.
* Add the ANDROID_HOME to PATH variable.

## Android uninstall server from device :
* adb uninstall io.appium.uiautomator2.server
* adb uninstall io.appium.uiautomator2.server.test

## adb commands
* https://www.androidcentral.com/10-basic-terminal-commands-you-should-know
* adb shell pm list packages - http://adbshell.com/commands/adb-shell-pm-list-packages
* Pull apk file from device : https://stackoverflow.com/questions/4032960/how-do-i-get-an-apk-file-from-an-android-device

## LaunchActivity name and package
To get information about the name of the package and the first activity that has to be launched for the testing
1. Browse through the **SDK folder -> Build-Tools -> Version folder**
2. Open cmd and execute command **./aapt dumb badging "path_to_apk"**
3. Find **package** (in the beginning of logs) and **launchable-activity** parameters



## Setup iOS
* Switch to WedDriverAgent folder **cd /usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver/WebDriverAgent/**
* Run **./Scripts/bootstrap.sh** for fetching dependencies
* And run **./Scripts/bootstrap.sh** if some issues with "no such file or directory"
* Run **open /usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver/WebDriverAgent/WebDriverAgent.xcodeproj**
* Add Apple-ID account in Xcode -> Preferences -> Account
* Download manual profiles
* Switch to WebDriverAgentRunner target in project settings
* Select your account in Sighing (Signing Certificate will be created)
* Run WebDriverAgentRunner on real device

## Certificates explanation
https://medium.com/ios-os-x-development/ios-code-signing-provisioning-in-a-nutshell-d5b247760bef

## Resolution for 'xcodebuild failed with code 65'
Clear DeriverData : *rm -f /Users/hanna_kokhanava/Library/Developer/Xcode/DerivedData*

## Fix issue 'xcodebuild failed with code 65' -  Xcode 9.3 + node 10.1.0 + Appium server 1.8.0
* Open the WebDriverAgent.xcodeproj
* Select 'Targets' -> 'WebDriverAgentRunner'
* Open 'Build Phases' -> 'Copy frameworks'
* Click '+' -> add 'RoutingHTTPServer' -> add 'YYCache.framework'
* https://github.com/facebook/WebDriverAgent/issues/902


## XCode version switching command
sudo xcode-select --switch /Applications/Xcode9.3.app

## ~/.bash_profile example :
* export JAVA_HOME="$(/usr/libexec/java_home)"
* export ANDROID_HOME=/Users/hanna_kokhanava/Library/Android/sdk
* export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools:$JAVA_HOME$
* export PATH=$PATH:/usr/local/bin/ 
