+++
title = "MD2K Software How-To: Getting Started"
description = "Details about the using the smartphone software and cloud"
keywords = []
+++


# Getting Started
mCerebrum is a suite of several Android applications that are combined with a set of configuration files. All source code is available at [MD2K's GitHub organization](https://github.com/MD2Korg).

These instructions will guide you in downloading, installing, and configuring the mCerebrum software suite using the default configuration to collect phone sensor data.


## Installation
1) Download the [latest version of mCerebrum](https://github.com/MD2Korg/mCerebrum-releases/raw/master/2.0/org.md2k.mcerebrum/mcerebrum.apk)
(found at this link or by using the QR code below) and install the APK file on an Android 5.0+ device.

<img src="/img/howto/mcerebrumQRcode.png">

2) Follow the on-screen instructions on your Android device to complete the installation.

3) When the installation is complete, open mCerebrum. You should see the home screen as shown here:

<img src="/img/howto/mC2DefaultHome.png">


## Install/Update Apps
mCerebrum uses a suite of software applications in conjunction with the main mCerebrum interface app. Follow these steps to download the latest versions of the apps in your mCerebrum suite.

You will need to download the **Storage** and **PhoneSensor** applications.

1) Open the *mCerebrum* app.

<img src="/img/howto/mcerebrumAppIcon.jpg">

2) From the mCerebrum home screen, tap *Application Install*.

<img src="/img/howto/applicationInstall50.png">

3) In the menu, find the *Storage* app and tap the green download button to download it. Follow the on-screen instructions to complete the installation.

<img src="/img/howto/storageDownload.png">

4) Return to the mCerebrum Application Install menu, find the *PhoneSensor* app and tap the green download button to download it. Follow the on-screen instructions to complete the installation.

<img src="/img/howto/phoneSensorDownload.png">



## Sensors Setup

1)	Open the *PhoneSensor* app.

<img src="/img/howto/phoneSensorIcon.png">

2) From the PhoneSensor home screen, tap the gear icon to open the Settings screen.

<img src="/img/howto/gearIcon1.png">

3) Use the Settings screen to select which phone sensors you would like to turn on/off. Tap the back button when finished.

<img src="/img/howto/phoneSensorSettings.png">

*Note*: To ensure high-quality data collection, the GPS feature of the smartphone must be set to High Accuracy Mode in your phone’s main settings (outside of the mCerebrum apps).


## <a name="startstop">Start/Stop Data Collection

1)	Open the *PhoneSensor* app.

<img src="/img/howto/phoneSensorIcon.png">

2) Tap the *START* button to begin data collection.

<img src="/img/howto/phoneSensorStart.png">

3) The button will now show a data collection timer. Tap the button again when you are ready to stop data collection.

<img src="/img/howto/phoneSensorStop.png">


## Visualize Real-Time Data

1)	Open the *PhoneSensor* app.

<img src="/img/howto/phoneSensorIcon.png">

2) From the PhoneSensor home screen, tap the visualization icon to open the Sensors screen.

<img src="/img/howto/visualIcon1.png">

3)	Select from the list of available sensors to visualize each set of data in real-time.

<img src="/img/howto/phoneVisualSensors.png">

4) Data will appear in a real-time plotter. Below is an example of the phone accelerometer data.

<img src="/img/howto/plotAccelData.png">


## <a name="backing"></a>Back Up Data on a Computer

1) **Important:** You must first stop data collection before transferring data to a computer. Open the PhoneSensor app and tap the button to stop data collection. See instructions [here]](#startstop) if you need more details.

2) Connect the smartphone to a PC using the charging cable.

<img src="/img/howto/mPerf/phone2computer.png">

3) Create a new folder on your computer where you would like to store the data.

4) Using the computer, navigate to the phone’s org.md2k.datakit folder. *[Phone > Android > data > org.md2k.datakit]*

5) Copy the org.md2k.datakit folder and paste it to the new folder you created.

6) Navigate to the phone’s log folder. *[Phone > log]*

7) Copy the log folder and paste it to the new folder you created. All sensor data is now saved to the computer.
