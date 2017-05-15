+++
title = "Under the Hood"
description = "Details about the software architecture, design, and developer-oriented interfaces"
+++

Intro goes here

# mCerebrum
The development and validation of new multisensory biomarkers and sensor-triggered interventions requires collecting raw sensor data and associated labels in the natural field environment. A software platform for such studies needs to not only support high-rate data ingestion, but also the entire sense-analyze-act pipeline at high-data rate.
We present, mCerebrum, a general-purpose mobile software platform for conducting such studies. It supports raw data collections from multiple high-rate sensors and real-time assessment of data quality to ensure data fidelity. It includes a scalable storage architecture to ensure quick response despite rapidly growing data volume. It provides efficient sharing of sensor data among multiple sources and sinks with flexibility to represent current and future data types while ensuring a high throughput. It implements the entire sense-analyze-act pipeline for concurrent computation of several multi-sensor digital biomarkers at high data rate by efficient reuse of computations. Finally, it has a reconfigurable scheduler that manages all prompts to participants that is burden- and context-aware.
With a modular design spanning 23+ apps, mCerebrum provides a complete ecosystem of system services and utility apps.
The design of mCerebrum is informed by its concurrent use in field studies at ten sites spanning 106,806 person days.

[More Information](mcerebrum)


# Cerebral Cortex
