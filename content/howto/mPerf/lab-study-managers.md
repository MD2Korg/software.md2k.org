+++
title = "Study: Admin"
description = "Details about saving participants' data from a study"
keywords = []
+++


# Overview

When a participant is finished with the study, please complete the following steps to sync the data to the cloud, shut down all applications, back up the data on a computer, and prepare the phone for the next participant.

**IMPORTANT NOTE:** The data files that are recorded by the phone are one hour in length before they are completed and a new file is started. This takes place at the top of every hour. (E.g., midnight, 1:00, 2:00—22:00, 23:00, etc.). This means you should **wait until the top of the hour AFTER completing a participant** (e.g., regardless if they are done at 14:01, 14:30, or 14:59, they must wait until 15:00 to sync data to the cloud).

# Contents

- [Sync Data to the Cloud](#syncing)
- [Stop Data Collection](#stopping)
- [Back Up Data on a Computer](#backing)
- [Prepare the Phone for the Next Participant](#preparing)


[Submit bug reports and feature requests](http://software.md2k.org/under-the-hood/feedback/)


## <a name="syncing"></a>Sync Data to the Cloud

1) From the main screen of the mCerebrum app, tap *Application Setup*.

<img src="/img/howto/mPerf/applicationSetup.png">

2) Find *Storage* in the list of applications, and tap the green *play* button to open the Storage/DataKit app.

<img src="/img/howto/mPerf/clearStorage.png">

**NOTE:** If applicable to your study, you will need to remove the GPS restrictions from the data stream before uploading. Do do this, tap the settings gear icon found in the upper-right corner of the app. Select *Upload Data* to open the Upload Data menu, then uncheck the *Location* box under *Restricted Data Stream*.

<img src="/img/howto/mPerf/restrictedDataUncheck.png">

3) Under the *Cerebral Cortex* header, tap the *Toggle* button to sync data to the cloud.

<img src="/img/howto/mPerf/DatakitToggle.png">

4) When you see the "Upload Complete" message, data syncing is now complete.

<img src="/img/howto/mPerf/DatakitUploadComplete.png">

**NOTE:** If applicable to your study, be sure to access the settings menu and re-check the *Location* box under *Restricted Data Stream* to enable GPS restrictions. This should be done after data upload is complete.

<img src="/img/howto/mPerf/restrictedDataChecked.png">


## <a name="stopping"></a>Stop Data Collection

1) Open the mPerf Study app.

<img src="/img/howto/mPerf/mPerfStudyIcon.png">

2) In the mPerf Study app, open the menu found in the upper-left corner.

<img src="/img/howto/mPerf/menuIcon.png">

3) Tap *Stop Data Collection*.

<img src="/img/howto/mPerf/stopDataCollection.png">

4) Tap *Yes* to confirm.

<img src="/img/howto/mPerf/stopDataConfirm.png">


## <a name="backing"></a>Back Up Data on a Computer

1) Connect the smartphone to a PC using the charging cable.

<img src="/img/howto/mPerf/phone2computer.png">

2) Create a new folder on your computer. (It may be helpful to use the participant’s user ID as the new folder name.)

3) Using the computer, navigate to the phone’s org.md2k.datakit folder. *[Phone > Android > data > org.md2k.datakit]*

4) Copy the org.md2k.datakit folder and paste it to the new folder you created.

5) Navigate to the phone’s log folder. *[Phone > log]*

6) Copy the log folder and paste it to the new folder you created. All study data is now saved to the computer.


## <a name="preparing"></a>Prepare the Phone for the Next Participant

#### Leave the study:

1) First open the mCerebrum app (by tapping the mCerebrum icon on the home screen or by tapping *Settings* in the mPerf app menu found in the upper-left corner).

<img src="/img/howto/mPerf/mCerebrumAppHome.png">

2) In the mCerebrum app, open the menu found in the upper-left corner.

<img src="/img/howto/mPerf/menuIcon.png">

3) Tap the User ID at the top of the menu next to the mCerebrum logo, then tap *Leave Study*.

<img src="/img/howto/mPerf/leaveStudyButton.png">

4) Tap *Yes* to confirm and leave the study.

<img src="/img/howto/mPerf/leaveStudyConfirm.png">


#### Delete the Database Storage:

1) From the mCerebrum app home screen, tap *Application Setup*.

<img src="/img/howto/mPerf/applicationSetup.png">

2) Find the Storage app in the list, and tap the Clear logo (red minus sign) to clear all data from Storage.

<img src="/img/howto/mPerf/storageMinus.png">

3) Tap *Yes* to confirm.

<img src="/img/howto/mPerf/deleteDatabaseFiles.png">


#### Join the Study with a New Participant:

1) On the mCerebrum home screen, tap *mCerebrum (click to join study)*.

<img src="/img/howto/mPerf/click2join.png">

2) On the next screen, enter the appropraite User ID and password for the user and tap *Login*.

3) When prompted, select the appropriate config file from the list.

4) After logging in, check to make sure all apps are installed and up-to-date (tap *Application Install* from the mCerebrum home screen, then tap the *Check Updates* button).
