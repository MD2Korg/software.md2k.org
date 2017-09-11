+++
title = "MD2K Software How-To: Adding New Sensors"
description = "Details about how developers can write a new mCerebrum application to collect data from a sensor"
keywords = []
+++


# Adding New Sensors

The MD2K software platform is open-source and welcomes contributions from anyone who is interested in improving mobile health. Developers are encouraged to add new sensors to our software platform. Please see below and visit our [MD2K GitHub organization](https://www.github.com/MD2Korg/) and [MD2K Under the Hood](http://software.md2k.org/under-the-hood/) pages for more information.

## How to Write a New mCerebrum Application to Collect Data from a Sensor or Wearable

**Table of Contents:**

1. [Download the latest version of mCerebrum](#head1)

2. [Prepare the Environment for Adding a New Sensor](#head2)

3. [Create a New Sensor Subclass](#head3)

4. [Implement the Methods File](#head4)

5. [Insert Code for Required Methods](#head5)

6. [Register the Sensor to the Sensor Manager](#head6)

With our open-source platform, you can add your own sensor as a built-in application for mCerebrum. This section describes how to develop and add your original sensor to our platform.

mCerebrum is a configurable software platform for mobile and wearable devices. The mCerebrum platform is divided into functional layers so that each component is flexible and can be adapted and extended without adversely affecting the other components. Two components – an access controller and data router – links each layer. The access controller is responsible to ensuring that pairs of components within the system have appropriate credentials to communicate with each other through the data router, which is responsible for routing data objects throughout the platform.

mCerebrum is primarily configured and controlled by a set of JSON configuration files. The configuration files inform the mCerebrum application how to handle data sources, notifications, conditions, and other various functions.

#### <a name="head1"></a>Download the latest version of mCerebrum
Download mCerebrum (http://mCerebrum.md2k.org) from GitHub and unzip the file folder. You can install the APK file on most Android devices.

#### <a name="head2"></a>Prepare the Environment for Adding a New Sensor
.



#### <a name="head3"></a>Create a New Sensor Subclass
.


#### <a name="head4"></a>Implement the Methods File
.


#### <a name="head5"></a>Insert Code for Required Methods
.


#### <a name="head6"></a>Register the Sensor to the Sensor Manager
.
