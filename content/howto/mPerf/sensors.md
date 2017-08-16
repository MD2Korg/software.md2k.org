+++
title = "mPerf User Guide - Sensors Overview"
description = "Overview of the mPerf sensors"
keywords = []
+++


# Sensors

The mCerebrum software platform is configurable for a wide variety of mobile and wearable sensors. This page shows an overview of the sensors currently integrated with the software for the mPerf project.

## Motionsense HRV Wrist Sensor

{{< figure src="/img/howto/MotionSenseHRV.png" title="Motionsense HRV Wrist Sensor" caption="">}}

Motionsense HRV is a wearable wrist sensor that integrates accelerometer, gyroscope, and magnetometer measurements. This can be used to track hand gestures and monitor activities such as smoking, eating, and brushing teeth. This sensor also measures heart rate using signals that are detected and classified into different classes of reliability, resulting in estimates of heart rate variability (HRV) and respective confidence levels.

#### How to Wear the Wrist Sensors

Put the Motionsense wrist sensors on as you would wear a watch or FitBit. The sensor should be oriented with the buckle on the strap going over the top of your wrist as shown.

{{< figure src="/img/howto/mPerf/WearingHRVright.jpg" title="Wearing the wrist sensors" caption="">}}

#### Troubleshooting
<center><iframe src="https://www.youtube.com/embed/2n7HwLWlgtQ" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></center>


If you are experiencing poor data quality:

- Reset the application, wait 15 seconds and check again.
- Restart the phone, wait one minute and check again.
- Make sure the wrist sensor is charged.

## Autosense Chest Sensor

{{< figure src="/img/howto/mPerf/AutoSenseChest.png" title="Autosense Chest Sensor" caption="">}}

Autosense chest sensor is a wearable unit with an elastic chestband and a set of connector cables. The sensor is designed to track breathing patterns by measuring respiratory effort and lung volume. These biomarkers of respiration can be used by the mCerebrum software to assist in monitoring and predicting repeated human behaviors such as stress, eating, speaking, and smoking.

#### Troubleshooting

If you are experiencing poor data quality:

- Make sure all cable connections are secure.
- Make sure the RIP connector is inserted into the correct port of the chest sensor.
- Tighten the chest band so it fits snugly under the armpits.
- Reset the application, wait 15 seconds and check again.
- Restart the phone, wait one minute and check again.
- Make sure the chest sensor is charged and powered ON.


## Phone Sensors

{{< figure src="/img/howto/mCerebrumOnPhone.png" title="Phone Sensors" caption="">}}

In addition to the sensors listed above, the mCerebrum software also utilizies many different sensors including in a smartphone itself. Each smartphone can provide valuable information through various sensors such as accelerometer, gyroscope, GPS, battery, and activity tracking.

#### Troubleshooting

If the mCerebrum app crashes perpetually (admin only):

- Clear all data from the DataKit app.
- Clear all data from the mCerebrum app.
- Delete the configuration folder located in the internal memory `/mCerebrum`
- Make sure you have installed the proper update for each app.
- Delete the mCerebrum app from the phone and re-install it.
