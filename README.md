<img src="https://s3.amazonaws.com/ionic-marketplace/wikitude-ionic-3-starter-app/screenshot_1.png" style="width:300px !important;"/> <img src="https://s3.amazonaws.com/ionic-marketplace/wikitude-ionic-3-starter-app/screenshot_2.png" style="width:300px !important;"/>
# ionic3-augmented-reality
This starter app is the fastest way to get you started with your own <strong>Augmented Reality</strong> projects and benefit from the powerful framework <strong>Ionic 3</strong>. It uses the version of the <strong>Phonegap/Cordova Wikitude Plugin (7.1)</strong> and is based on <strong>Ionic 3 (3.19.0)</strong>. It contains two sample AR Worlds (1 Geo World - default, and one Image Recognition World) from the Wikitude sample projects (a 3D model of the Earth floating on a relative location). <p>You can easily replace this sample with other samples from the Wikitude SDK Examples directory, by replacing the content of the directory <strong>src/assets</strong> with another sample. (See Wikitude SDK --> WikitudeSDK_Android_7-1-0_2017-09-20_19-46-00/Examples/SDKExamples/wikitude-sdk-samples/src/main/assets/samples Note: when copying a sample directory to your project, replace the $-signs with underscore characters, and update the path in <strong>src/pages/ar-view/ar-view.ts</strong>.)<p>
You can switch between the sample geo world and the sample IR world in the file <strong>src/pages/ar-view/ar-view.ts</strong> and comment in the lines marked with (1) for the IR sample world, or (2) for the sample GEO world - don't forget to comment out the other sample world (IR or GEO), as you can't have a GEO world and a IR world at the same time.<p>
For the IR world, please use target 3 of <a href="http://www.wikitude.com/external/doc/documentation/5.0/android/images/target_images_examples.pdf">Wikitude Target Examples</a>.<p>
Additionally this Starter app shows you how to communicate between the ionic 3 pages and the Wikitude SDK: There is a "Snapshot" link on the AR view. When you click it, a message is sent to a callback defined in <strong>app.components.ts</strong>, this function then creates a snapshot of the screen and saves it on the phone. Look for "<strong>captureScreen</strong>" within the sources. After the image has been saved locally, a Javascript function within the Wikitude SDK is called from Ionic using <strong>WikitudePlugin.callJavaScript(...)</strong>, as an example of how you can send massages the other way round, from Ionic to the Wikitude SDK.<p>  

## Version Information
1.0 Initial creation for Ionic 2 RC.0 - Oct 6, 2016<br>
1.1 Upgrade to Ionic 2 RC.4; added an IR sample world - Jan 12, 2017<br> 
1.2 Upgrade to Ionic 2 RC.5 - Jan 16, 2017<br> 
1.3 Upgrade to Ionic 2 (2.0.1-final) and Wikitude 6.0 - Jan 26, 2017<br> 
1.4 Upgraded to Ionic 2 (2.3.0) - March 25, 2017<br> 
1.5 Upgraded to Ionic 3 (3.0.1) - April 25, 2017<br> 
1.6 Upgraded to Ionic 3 (3.19.0) - Dec 15, 2017

## How to use this template

1) To get started with ionic, see https://ionicframework.com/docs/intro/installation/<br>

2) Create an empty tab app by typing in the terminal

```bash
$ ionic start Ionic3ARApp
```

```bash
What starter would you like to use: tabs
Would you like to integrate your new app with Cordova to target native iOS and
 Android? Yes
Install the free Ionic Pro SDK and connect your app? No
```

3) Using the terminal, go to the directory Ionic3ARApp and and open the file config.xml and change the path unter widget id="your own path". This is going to be the Android package id and the IOS Bundle Identifier. A good editor for Ionic is Visual Studio Code (The command to open is "code .") <br>

```bash
$ cd Ionic3ARApp
code .
```

4) Now add the platform iOS

```bash
$ ionic cordova platform add ios
```

5) Then add the android platform as well <br>

```bash
$ ionic cordova platform add android
```

6) Now it's a good time to test the new apps.

```bash
$ ionic cordova build android
```

```bash
$ ionic cordova build ios
```

For iOS, at this point I open XCode and then open the file 
/path_to_your_project/Ionic3ARApp/platforms/ios/Ionic3ARApp.xcodeproj<br>

For Android you can install your app like this:
adb install -r /path_to_your_project/Ionic3ARApp/platforms/android/build/outputs/apk/android-debug.apk<p>

If everything goes well so far, you're good to go to add Wikitude:<br>

7) Download this starter app (it's a <strong>src</strong> directory), and replace the <strong>src</strong> directory of the empty tab app with it<br>


8) Install the Wikitude Cordova Plugin:

```bash
$ ionic plugin add https://github.com/xiwei328/ionic3-augmented-reality.git
```

9) Obtain a (free) license key from Wikitude: Go to http://www.wikitude.com/developer/licenses, register, and download a key for the Wikitude SDK. Then copy the key to the file `src/app/app.component.ts`

10) For iOS, open xcode, under Resources/Ionic3ARApp-Info.plist add the following values:

<strong>NSCameraUsageDescription</strong> and in the value field enter something like like "This app needs the camera for Augmented Reality."<br>
<strong>NSLocationWhenInUseUsageDescription</strong>, and a value like "This app needs your location for Geo AR"<br>
<strong>NSPhotoLibraryUsageDescription</strong>, and a value like "This app needs to access your photo gallery such that you can share your screenshots"<br>
<strong>NSPhotoLibraryAddUsageDescription</strong>, and a value like "This app needs to access your photo gallery such that you can share your screenshots"<br><br>

11) Please remember that you can't test this plugin on a browser or emulator. You need an Android or iOS device. To test on Android, type:

```bash
$ ionic build android
```
and install the apk (see filename when the compilation finished), type: 

```bash
$ adb install -r your-path-to-your-apk-file
```

To test on iOS, compile your project with 

```bash
$ ionic build ios
```

Then you can open `Ionic3ARApp/platforms/ios/Ionic3ARApp.xcodeproj` with XCode, then you plug in you IOS device, then in XCode, on the top left, click `Ionic3ARApp`, popup opens, choose your device, and then click the Build button (the triangle on the top left). When you are installing the app using XCode for the first time, you need to set a <strong>Team</strong>, under <strong>Project Settings --> General --> Signing --> Team</strong>, choose your Apple ID.

<strong>Logging</strong>: to view the logs of your AR world, click on the orange triangle on the bottom right of the AR View. Logs are printed bottom to top. To remove the orange triangle, remove the following from src/assets/07_3dModels_6_3dModelAtGeoLocation/index.html: Take this out of your body statement: <strong>onLoad="javascript:AR.logger.activateDebugMode();"</strong>

To learn more about how to develop your own AR worlds, please look at http://www.wikitude.com/developer/documentation/phonegap.
