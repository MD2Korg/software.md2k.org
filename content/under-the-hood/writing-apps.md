+++
title = "How to Write a New mCerebrum Application"
description = "Details about how developers can write a new mCerebrum application to collect data from a sensor"
keywords = []
+++

# How to Write a New mCerebrum Application
## to Collect Data from a Sensor or Wearable

With our open-source platform, you can add your own sensor as a built-in application for mCerebrum. This section describes how to develop and add your original sensor to our platform.

mCerebrum is a configurable software platform for mobile and wearable devices. The mCerebrum platform is divided into functional layers so that each component is flexible and can be adapted and extended without adversely affecting the other components. Two components – an access controller and data router – links each layer. The access controller is responsible to ensuring that pairs of components within the system have appropriate credentials to communicate with each other through the data router, which is responsible for routing data objects throughout the platform.

##### Quick start
1.	Download the latest version of mCerebrum (http://mCerebrum.md2k.org4) and install the APK file on and Android 5.x or 6.x device.
1.	mCerebrum will run and the Settings button will be highlighted in red, press it.
1.	A prompt will be shown asking you to enter a filename of a configuration file to download, enter *default* and press OK.
1.	Once a configuration file is successfully downloaded and installed, you will be prompted with an Admin password screen. The default password is *1234*.
1.	Congratulations, you have successfully installed the main mCerebrum application.

mCerebrum is primarily configured and controlled by a set of JSON configuration files. The configuration files inform the mCerebrum application how to handle data sources, notifications, conditions, and other various functions.
