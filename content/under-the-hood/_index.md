+++
title = "Under the Hood"
description = "Details about the software architecture, design, and developer-oriented interfaces"
+++

# Motivation

{{< figure src="/img/under-the-hood/md2k_motivation.png" title="Raw sensor data is required for the development of new mHealth biomarkers." caption="">}}
The reason that commercial systems only provide biomarkers is that they have already gone through the Sense-Markers-Intervention process which allows them to only expose biomarker data.  This provides limited value for a biomedical researchers due to the reliance on generally proprietary algorithms that compute these biomarkers and the limited amount of data generated.

The development and validation of any new mHealth biomarker, however, requires conducting research studies in lab and field settings and collecting raw sensor data with appropriate labels such as self-reports. Raw sensor data is of increasing interest to research studies as it significantly increases the useful life of the information collected. Similar to biomedical studies that often archive bio specimens in biobanks so that they can be reprocessed to take advantage of future improvements in assays and support biomedical discoveries not possible at the time of data collection, raw sensor data can be used to obtain new digital biomarkers that were not available at the time of data collection. Doing so, however, requires a mobile phone software platform that can be used to collect both high-rate raw sensor data and associated labels in the field.

## System Overview

{{< figure src="/img/under-the-hood/use_case.png" title="System Overview" caption="There are three core users of mCerebrum and Cerebral Cortex. (1) The user wearing sensors and interacting with mCerebrum which uploads data to Cerebral Cortex, (2) the health science researcher that conduct studies, visualize field data, run population-scale analysis, and (3) the data science researcher that constructs models through machine learning, runs interative analysis through web-based dashboards, and buils scalable data analytics across large populations.">}}


# mCerebrum: Sense-Analyze-Act for Mobile High Frequency Wearable Sensors
<img src="/img/under-the-hood/mCerebrum.png" style="height: 200px; float: left;">
The development and validation of new multisensory biomarkers and sensor-triggered interventions requires collecting raw sensor data and associated labels in the natural field environment. A software platform for such studies needs to not only support high-rate data ingestion, but also the entire sense-analyze-act pipeline at high-data rate.
We present, mCerebrum, a general-purpose mobile software platform for conducting such studies. It supports raw data collections from multiple high-rate sensors and real-time assessment of data quality to ensure data fidelity. It includes a scalable storage architecture to ensure quick response despite rapidly growing data volume. It provides efficient sharing of sensor data among multiple sources and sinks with flexibility to represent current and future data types while ensuring a high throughput. It implements the entire sense-analyze-act pipeline for concurrent computation of several multi-sensor digital biomarkers at high data rate by efficient reuse of computations. Finally, it has a reconfigurable scheduler that manages all prompts to participants that is burden- and context-aware.
With a modular design spanning 23+ apps, mCerebrum provides a complete ecosystem of system services and utility apps.
The design of mCerebrum is informed by its concurrent use in field studies at ten sites spanning 106,806 person days.

<div class="row">
  <!-- 16:9 aspect ratio -->
  <div class="embed-responsive embed-responsive-16by9">
    <iframe allowFullScreen='allowFullScreen' class="embed-responsive-item" src="https://www.youtube.com/embed/ENngs9eL4VQ?controls=2&showinfo=0"></iframe>
  </div>

</div>

[More Information](mcerebrum)


# Cerebral Cortex: Population-scale Model Learning and Data Analytics
<img src="/img/under-the-hood/Cerebral Cortex.png" style="height: 200px; float: left;">
Cerebral Cortex is the big data companion of mCerebrum designed to support population-scale data analysis, visualization, model development, and intervention design.  It is capable of scaling 1,000s of concurrent mCerebrum instances and supports machine learning model development on population-scale data sets and interoperable interfaces for aggregation of diverse data sources.  Currently Cerebral Cortex supports 10 concurrent [studies](/deployments) combining 2,100+ partiicpants, 100,000+ person-days of data and 4.7 trillion data points (100+TB).
