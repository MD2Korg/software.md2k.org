+++
title = "mCerebrum"
description = "Details about the software architecture, design, and developer-oriented interfaces"
keywords = []
+++

<div class="row">
  <!-- 16:9 aspect ratio -->
  <div class="embed-responsive embed-responsive-16by9">
    <iframe allowFullScreen='allowFullScreen' class="embed-responsive-item" src="https://www.youtube.com/embed/GR3pahhXp4U?controls=2&showinfo=0"></iframe>
  </div>

</div>

<!-- {{< youtube id="GR3pahhXp4U" controls="2" showinfo="0" >}} -->

Activity trackers and smartwatches that provide daily activity and calorie expenditure biomarkers and geoexposures from GPS are being incorporated in various research studies. They have advanced health research and led to novel interventions to improve health and wellness. Given the tremendous potential of mobile sensors to monitor a wide variety of daily exposures, behaviors, symptoms, and health outcomes[1], several new digital mobile health (mHealth) biomarkers are emerging. They include the detection of eating, smoking, stress, craving, depression, seizures, among others.

Development and validation of any new mHealth biomarker, however, requires conducting research studies in lab and field settings and collecting raw sensor data with appropriate labels (e.g., self-reports). Raw sensor data is of increasing interest to research studies as it significantly increases the useful life of the information collected. Similar to biomedical studies that often archive biospecimens in biobanks so that they can be reprocessed to take advantage of future improvements in assays and support biomedical discoveries not possible at the time of data collection, raw sensor data can be used to obtain new digital biomarkers that were not available at the time of data collection. Doing so, however, requires a mobile phone software platform that can be used to collect both high-rate raw sensor data and associated labels in field.

A general-purpose software platform that can enable such data collection needs several attributes.

1. It must support concurrent connections to a wide variety of high-rate wearable sensors with an ability to plug-in new sensors.
2. It must ingest the large volume of rapidly arriving data for which native support does not yet exist in the smartphone hardware or operating system without falling behind and losing data.
3. It needs to support reliable storage of quickly growing volume of sensor data, whose archival is critical to development and validation of new biomarkers.
4. It is desirable to quickly analyze incoming data to monitor data quality so any errors in sensor attachment or placement can be fixed quickly to maximize data yield.
5. It needs to support the sense-analyze-act pipeline for high-rate streaming sensor data. This is necessary to prompt self-reports (for collection of labels) as well as confirm/refute prompts for validation of new biomarkers in the field. Sense-analyze-act support is also needed to aid development and evaluation of sensor-triggered interventions.
6. It needs seamless sharing of streaming data from multiple sensors to enable computation of multi-sensor biomarkers (e.g., stress, smoking, eating).
7. The platform needs to be general-purpose and extensible to support a wide variety of sensors, biomarkers, and study designs.
8. It needs to be architecturally scalable so that it can support concurrent computation of a large number of biomarkers (each of which requires complex processing) without saturating the computational capacity or battery life of the mobile phone.
9. It needs to carefully control interruptions to study participants from various sources (e.g., self-report, ecological momentary assessment (EMA) and interventions (EMI), fixing sensor attachments) limiting user burden and cognitive overload, while satisfying the numerous study requirements.


{{< figure src="../../img/mcerebrum/frameworks.png" title="Framework comparisions" caption="Commercially-available software platforms for conducting research studies such as ResearchKit[2] and HealthKit[3] are optimized to collect self-reports and digital biomarkers (e.g., calories, steps, blood pressure, glucose level) and are not suitable for collecting high-rate sensor data. Several research groups have developed their own versions of such software platforms, but these are often specific to target biomarkers and not easily extensible.">}}


*mCerebrum* is an open-source, generalizable, and reusable platform that meets all the above requirements. It is deployed in ten research studies with unique study designs and for multiple health targets. It comes with out-of-the-box support for wrist-worn inertial sensors, physiological sensors worn on the chest, sensors in a smartphone (e.g. GPS), weight and blood pressure monitors, and smart toothbrushes, and provides software interfaces to let developers easily incorporate additional ones. mCerebrum supports high-frequency raw sensor data collection in excess of 800 Hz or 70+ million samples/day, along with their curation, analysis, storage (2GB/day), and secure uploads to a cloud platform. Because it must work in resource-poor settings (several of current studies are with low-income participants), mCerebrum is built to operate the entire sensor-analyze-act pipeline locally, without a constant data connections. It continuously assesses data quality to quickly identify and resolve issues by correcting sensor detachment or misplacements on the body. It supports high-rate streaming data collection from multiple sensors, real-time computation of several multi-sensor biomarkers, sensor-triggered interventions, as well as collection of self-reports prompted by real-time biomarkers computations (e.g., confirm/refute). Several biomarkers computed in real-time on the phone (e.g., stress, smoking) trigger Just-in-Time Adaptive Interventions (JITAI)[4].


---
Add link to these citations

> 1. Santosh Kumar, Wendy Nilsen, Misha Pavel, and Mani Srivastava. 2013. Mobile health: Revolutionizing healthcare through transdisciplinary research. Computer 46, 1 (2013), 28–35.
> 2. Apple’s ResearchKit. 2017. Online at http://www.researchkit.org/. , visited April (2017).
> 3. Ari Y Benbasat and Joseph A Paradiso. 2007. A framework for the automated generation of power-efficient classifers for embedded sensor nodes. In Proceedings of the 5th international conference on Embedded networked sensor systems. ACM, 219–232.
> 4. Inbal Nahum-Shani, Shawna N Smith, Ambuj Tewari, Katie Witkiewitz, Linda M Collins, Bonnie Spring, and S Murphy. 2014. Just in time adaptive interventions (jitais): An organizing framework for ongoing health behavior support. Methodology Center technical report 14-126 (2014).
