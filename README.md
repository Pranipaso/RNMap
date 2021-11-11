<!-- version https://git-lfs.github.com/spec/v1
oid sha256:a450be8f265a9244eb2ac223306fddba7669b8f4fc71ff5b4a0340684f2cce53
size 3048
 -->
 
 
 <!-- version https://git-lfs.github.com/spec/v1
oid sha256:e8e5b143921e273aac80d46ee98bf3f4806fea124a946a9c724c1f3612896095
size 2909 -->
# Android

### Generate the api key
https://console.cloud.google.com/

### Add the following
##### In `build.gradle` file of the project, add these inside dependencies

    classpath "com.android.tools.build:gradle:7.0.3"
    classpath "com.google.android.libraries.mapsplatform.secrets-gradle-plugin:secrets-gradle-plugin:2.0.0"

##### In `build.gradle` file of your app

At the top of the file

    apply plugin: "com.google.android.libraries.mapsplatform.secrets-gradle-plugin"

Add the dependency

    implementation 'com.google.android.gms:play-services-maps:17.0.1'

##### In `Manifest` file

Add <meta-data ...> before the `activity` tag

    <Manifest>
    <Application
    	....
    	....
    	....
		>
		 <meta-data
			android:name="com.google.android.geo.API_KEY"
			android:value=“api_key_generated” />
		<Activity>
			......
		</Activity>
    </Application>
    </Manifest>

Add these permissons

    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>

##### In the gradle.wrapper.properties 

>change the gradle version to 7.0.2

#### Make sure you have JDK version 11 or greater in your app

###### If you don't know the java version then,

>Select `Project Structure` from file menu -> then select `SDK Location` menu

>you can see a text `"JDK Location was moved to Gradle Settings" `

>click on the `gradle settngs` , it will redirect you to the jdk location where you'll be able to see the JDK version and also you can change the version from there.

# IOS
#### In the `AppDelegate.m` file

###### Add the following


    @import GoogleMaps;
    ......
    ......
    ......
    -(BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary 	*)launchOptions {
    		...
    			[GMSServices provideAPIKey:@"API KEY GENERATED"]; // add this line
    		...
    	}

##### `cd ios and pod install`

#### Usage
###### In the ` <Pimap>`  component passing region is necessary along with the style containing height and width.
    
        var region = {
              latitude: 37.78825,
              longitude: -122.4324,
              latitudeDelta: 0.1,
              longitudeDelta: 0.1,
              radius: 10, // In KiloMeters
            };
    
        <Pimap region={region} style={{height:'100%',width:'100%'}}/>
    

#### Errors Appeared

###### After installing the library and running the application your project is getting the error `Unable to resolve the module plusinfosys-maps` or `unable to find the plusinfosys-maps within node_modules`

##### Solution

>go to your project's node_modules folder and find the library you installed, in our case it's plusinfosys-maps, back up it either by copying or cutting it and delete the folder and then create a folder with the same name and paste it

###### again `cd ios and pod install`

##### Your Project will run fine.
