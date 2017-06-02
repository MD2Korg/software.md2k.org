+++
title = "mCerebrum::Architecture"
description = "Details about the software architecture, design, and developer-oriented interfaces"
keywords = []
+++

To achieve our goal of high-rate streaming data collection, logging, real-time processing, and intervention, we built a flexible, layered architecture.

{{< figure src="/img/under-the-hood/mcerebrum/mc_overview.png" title="Architecture Overview" caption="mCerebrum overview illustrating how high-frequency data, 800+ Hz, is processed and includes components for real-time data quality assessment, privacy, model evaluation, biomarker computation, and triggered user engagement.">}}
mCerebrum supports high-frequency raw sensor data collection in excess of 800 Hz or 70+ million samples/day, along with their curation, analysis, storage (2GB/day), and secure uploads to a cloud platform. Because it must work in resource-poor settings (several of current studies are with low-income participants), mCerebrum is built to operate the entire sensor-analyze-act pipeline locally, without a constant data connections. To meet these needs, mCerebrum has nine key capabilities:

1. Concurrent connection to a wide variety of high-rate wearable sensors with an ability to add new sensors
2. Ingest a large volume of rapidly arriving data for which native support does not yet exist in the smartphone hardware or operating system
3. Quickly analyze incoming data to monitor for data quality problems so that errors can be corrected
Reliable storage of quickly growing volume of sensor data, whose archival is critical to the development and validation of new biomarkers
4. Control interruption to study participants (Self-report, Ecological Momentary assessments (EMA), and interventions (EMI)) limiting burden and cognitive overload while satisfying the numerous study requirements.
5. Support a Sense-Analyze-Act pipeline for high-rate streaming sensor data
		1. self-report and confirm/refute prompts
		2. Development and evaluation of sensor-triggered interventions
6. Seamless sharing of streaming data from multiple sensors to enable computation of multi-sensor biomarkers (stress, smoking, eating)
7. Architecturally scalable to support concurrent computations of a large number of biomarkers without saturating the computation capacity or battery life of the mobile phone
8. General-purpose and extensible to support a wide variety of sensors, biomarkers, and study designs



The architecture is composed of five layers:

1. **Communication interfaces** which include support for both smartphone sensors and wearable sensors
2. **Data sources** that provide an interface between devices and the rest of the mCerebrum platform
3. **Storage and routing interface**, which provides persistent data storage and routing of intermediate results among the various components and is subject to the rules of a privacy controller
4. A **signal processing** layer provides the necessary support for long-running applications to receive and process data from elsewhere in the system
5. The **participant interface** layer that implements all interactions with the participants.

{{< figure src="/img/under-the-hood/mcerebrum/mCerebrum_paper.png" title="Architecture" caption="mCerebrum's architecture consists of 5 layers: (1) Communication, (2) Data Sources, (3) Storage, (4) Signal Processing, and (4) Participant Interaction, all connected through a data router. The colors indicate different categorizations of applications with red for high-rate and orange for low-rate sensors, blue indicates core components of mSense, cyan for system services, and green represents participant-centric applications.">}}



Together, they represent 23+  applications across our currently supported studies.

<table class="table table-hover">
	<thead>
		<th>Application</th>
		<th>Description</th>
	</thead>
	<tbody>
		<tr>
			<th scope="row">DataKit</th>
			<td>Handles routing, privacy, and storage</td>
		</tr>
		<tr>
			<th scope="row">DataKitAPI</th>
			<td>API library for apps to use DataKit</td>
		</tr>
		<tr>
			<th scope="row">Plotter</th>
			<td>Real-time data visualizer</td>
		</tr>
		<tr>
			<th scope="row">Privacy Controller</th>
			<td>Allows the participant to suspend data collection and EMA prompting</td>
		</tr>
		<tr>
			<th scope="row">Utilities</th>
			<td>Common helper functions for mCerebrum</td>
		</tr>

		<tr>
			<th scope="row">Phone</th>
			<td>Integrates the smartphone sensors</td>
		</tr>
		<tr>
			<th scope="row">Chestband (AutoSense)</th>
			<td>Data collection from ANT+ sensor suite</td>
		</tr>
		<tr>
			<th scope="row">Wrist (MotionSense, MotionSenseHRV)</th>
			<td>BLE wrist-worn motion capture device</td>
		</tr>
		<tr>
			<th scope="row">iCO</th>
			<td>Carbon Monoxide sensor for in-the-field validation</td>
		</tr>
		<tr>
			<th scope="row">Smartwatch (Microsoft Band, Android Wear)</th>
			<td>Bluetooth 4 connected watch</td>
		</tr>
		<tr>
			<th scope="row">UWB RF (EasySense)</th>
			<td>BLE chest sensor for measuring heart function and lung fluid</td>
		</tr>
		<tr>
			<th scope="row">Blood Pressure (Omron)</th>
			<td>BLE-connected blood pressure cuff</td>
		</tr>
		<tr>
			<th scope="row">Weight (Omron)</th>
			<td>BLE-connected weight scale</td>
		</tr>
		<tr>
			<th scope="row">Smart Toothbrush (Oral-B)</th>
			<td>BLE-connected smart toothbrush</td>
		</tr>

		<tr>
			<th scope="row">Stream Processor</th>
			<td>Provides real-time computation of biomarkers (e.g. stress, smoking, activity, etc...)</td>
		</tr>

		<tr>
			<th scope="row">Mood Surfing</th>
			<td>A custom built stress reduction app</td>
		</tr>
		<tr>
			<th scope="row">Thought Shakeup</th>
			<td>A custom built stress reduction app</td>
		</tr>
		<tr>
			<th scope="row">Medication</th>
			<td>Medication adherence compliance app and reminder system</td>
		</tr>
		<tr>
			<th scope="row">Self Report</th>
			<td>Customizable self-report prompts</td>
		</tr>
		<tr>
			<th scope="row">EMA</th>
			<td>Customizable survey (EMA) delivery application</td>
		</tr>

		<tr>
			<th scope="row">Study</th>
			<td>Main study interface; provides an application management framework for the rest of the applications</td>
		</tr>
		<tr>
			<th scope="row">Scheduler</th>
			<td>Customizable scheduling system for delivering prompts to a participant based on biomarker and other inputs</td>
		</tr>
		<tr>
			<th scope="row">Adherence Reminder</th>
			<td>A custom variant of EMA/EMI scheduler to remind data collection from episodic sensors</td>
		</tr>
		<tr>
			<th scope="row">Notification Manager</th>
			<td>Acts as the gatekeeper for all user prompts to manage user burden</td>
		</tr>
	</tbody>
</table>

## Real-Life Deployments

The design of mCerebrum has emerged from half a decade of experience in supporting half a dozen completed field studies at independent sites. The current design of mCerebrum is in various stages of deployment in ten research studies at independent sites throughout the United States. These studies collectively span a total of 2,251 unique participants and 106,806 person-days (2.5 million hours) of high-frequency sensor data. We estimate the net data generated, processed, stored, and transmitted will be over 100TB and about 4.7 trillion data points based on our current data abstraction. Deployments are listed [here](/deployments) and provide a breakdown of these studies. We briefly describe each study to show the diverse studies adequately served by mCerebrum.

The smoking studies involve participants who want to quit smoking. They participate in the study for four days prior to quitting and 10 days after quitting while smoking, eating, stress, activity, and geoexposures are monitored.  The heart failure study tracks activity, eating, medication adherence, lung fluid change, blood pressure, and weight for 30 days. The cocaine study tracks cocaine use, stress, activity, and smoking activity for two weeks in a field setting. The oral health study tracks brushing and flossing behavior on a drug use population to predict their effect on plaque accumulation over six months. The behavior change study tracks stress, smoking, eating, sleep, and activity for smokers and obese participants for 14 days. The job performance study will monitor 800 employees on their task performance, citizenship, and counterproductive behaviors for ten weeks.

All studies involve continuous data collection from two wrist sensors and smartphone sensors. The smoking studies, cocaine study, behavior change study, and the job performance study also involves continuous data collection from a chest band. All smoking studies involve computation of stress and smoking events on the phone which are used to launch stress intervention based on a micro-randomized trial design. In the pilot phase one study, smoking detection is used to prompt a confirm/refute question.

All smoking studies involve generating EMA prompts based on random prompts and in response to detection of stress and smoking. One EMA of each type must be delivered within each four hour block of the day between start and end times of the day as selected by the participants. Since responding to an EMA results in an incentive payment, EMA prompts are to be generated only when the data quality from sensors are acceptable several minutes preceding the EMA prompt and the participant is not engaged in activities such as exercising or driving a vehicle. Also, successive EMA or EMI prompts are to be separated by a minimum time gap to limit burden. Finally, participants have an option to suspend data collection from specific sensors and suspend prompt generation for privacy purposes.

In all studies, the majority of mCerebrum's components are reused and configuration files are the only thing that must be changed.  Sometimes study requirements necessitate the need for custom programmed logic and whenever possible, this is generalized and incorporated in the the main components for the benefit of other studies, both current and future.


### Key Features of mCerebrum
As the description of the ten studies shows, mCerebrum has been designed as a general-purpose platform that can support the development and validation of mHealth biomarkers and sensor-triggered interventions. It incorporates the complete pipeline of sense-analyze-act for high-rate streaming data from multiple sensors. Coupled with scalable storage, it supports concurrent real-time computation of data quality and several multi-sensor biomarkers, and manages burden- and context-aware interaction with participants to collect self-reports and deliver sensor-triggered interventions.



## Sense

The sensing layer is responsible for reliable collection, storage, and sharing of streaming sensor data from multiple sensors. The first major challenge is to provide high throughput to handle the incoming data rate from multiple concurrently connected sensors via multiple radios while providing flexible representations to accommodate current and future data types and their associated metadata. The second challenge is to allow efficient sharing of incoming data among multiple sources and recipients, while maintaining a high throughput. The third challenge is to provide storage support that maintains query responsiveness in the face of rapidly growing data.

We first describe _DataKit_ and how it provides computation and communication efficiencies that allow the handling of high-frequency data rates. Next, we describe our scalable storage design that addresses the capabilities necessary to maximize the amount of data collected and stored within the system.

### DataKit: Efficient Collection & Sharing of High-rate Sensor DataKit

mCerebrum's DataKit is designed to collect high-rate sensor data from multiple concurrent sources and allow efficient many-to-many sharing of data between data sources and sinks. Because data sources will grow in diversity of data types and likewise recipients may accept different formats of data from double values to complex JSON encoded Ecological Momentary Assessments (EMAs), DataKit provides a flexible structure to handle data representations and transport within the system. Additionally, by providing a fast and efficient communication mechanism, computation can be reused by transmitting intermediate results through DataKit for other processes to utilize instead of requiring each application to compute values as needed.

DataKit is implemented as a data router instead of utilizing a common database for storage due to two key limitations.  First, SQLite, the de facto standard for Android, is unable to [efficiently scale]({{< relref "#scalable-storage-of-high-rate-sensor-data" >}})  to the data rates mCerebrum requires. Second, having a central controller allows for better control over security and privacy of data streams, restricting which information is persisted and stored through dedicated APIs.

#### Data representations
mCerebrum's data model is built on two abstractions: (1) a _data point_, which is the tuple consisting of a timestamp and value and (2) a _data stream_, a uniquely identifiable collection of data points.
A data point value can be composed of any of the following: _boolean_, _integer_, _long_, _double_, _string_, _JSON_, and all _array_ variants.  By constraining most data to primitive types, we allow for efficient serialization and communication while allowing for complex data types through JSON encoding.


#### Flexible and efficient communication
mCerebrum provides a simple, yet flexible and efficient, communication mechanism through DataKit and DataKitAPI.  The API implements functionality common to many publish-subscribe mechanisms with additional support for sending query commands through the interface. It allows an application to _connect_ and _disconnect_ from DataKit and provides a _subscribe_ and _unsubscribe_ mechanism.  In order to search for data streams, it provides a _find_ method that allows for partial matching of the data stream based on included metadata.  _Subscribe_ utilizes a callback mechanism which allows DataKit to directly route appropriate data through function callbacks.  Applications can _query_ by the last $N$ samples and by time-range to retrieve information from DataKit.  In order to create a data stream and its associated metadata, _registration_ and _unregistration_ methods are provided.  Finally, an _insert_ method is provided to send data to DataKit.  These basic building blocks allow for a variety of applications to be constructed and their simplicity keeps internal complexity down to ensure efficient data processing and routing.

Smartphone resource constraints make communication efficiency crucial to handling high-frequency data.  Android runs applications as separate processes for security and quality-of-service reasons; however, this introduces the need for inter-process communication (IPC) which is provided through three different mechanisms: _Intents_, which are implemented as a message forwarding system but suffers from performance issues with high-frequency data due to high resource utilization and latency; _anonymous shared memory_, is only suitable for sharing small amounts of data due to its dependence on mutually accessible RAM; and _Binder_, is a Remote Procedure Call (RPC) mechanism that allows for callback methods to be defined and is utilized by mCerebrum.  The Binder mechanism has a shared system transaction buffer of 1MB and it is critical that serialization, processing, and communications related to the Binder mechanism be as efficient as possible to ensure the buffer does not overflow.  An initial attempt at utilizing RPC to route data through the system resulted in an overflow of this buffer due to too many outstanding transactions when we sent unique requests for each data point. To resolve this overflow, a data buffer was introduced for high-frequency data streams inside DataKitAPI to ensure that each application receives data in the correct order and it automatically buffers data as appropriate to meet performance requirements.

{{< figure src="/img/under-the-hood/mcerebrum/flexibility.png" title="Comparison of different platforms" caption="Each platform is represented by an arrow illustrating the bandwidth of the platform and extending right showing flexibility of data representation starting at the number of core data types supported.">}}

We evaluated the performance of mCerebrum for high-rate data handling and compared it with Google Fit[1], AWARE[2], and HealthKit[3]. For Google Fit and AWARE, we used a Samsung S5 running Android 5.1.1 and for HealthKit, we used an iPhone 5s running iOS 10.2.1. In all cases, a sample application was written to generate synthetic data and store it within the frameworks with varying buffer sizes.

The buffer size and data rate were both increased until failure. Google Fit yielded 1,560 samples per second with HealthKit maxing out at 1,100 samples per second. The AWARE framework suffers from a lack of built-in support for batch operations, resulting in a maximum throughput of 260 samples per second. mCerebrum, in contrast, achieves 4,500 samples per second.

Query performance degraded similarly in existing platforms due to their reliance on SQLite as a primary storage container for the data. We discuss this in more detail in the [storage section]({{< relref "#scalable-storage-of-high-rate-sensor-data" >}}).
In summary, mCerebrum provides data representations that result in both high-throughput and flexibility by allowing varying storage abstractions giving the platform high performance and flexibility.


#### Handling data representation diversity

Wearable sensors are still in early stages of data standardization. Some commercial devices such as Microsoft Band or Zephyr Bioharness provide APIs to send and receive data in well-understood formats. However, in other cases, devices send raw data directly from the sensors and require further interpretation based on their specifications. Depending upon the radio technology and API implementation, data could arrive in blocks associated with a single timestamp or samples cold be timestamped individually.

{{< figure src="/img/under-the-hood/mcerebrum/Data_Sources_paper.png" title="Currently Supported Data Sources" caption="mCerebrum supports sensors ranging from 2 samples/day to 300 Hz per device including: BLE (green), Bluetooth 4.0 (red), ANT+ (orange), and internal (yellow).  Additionally, it support short audio and video clips with a high data rate storage mechanism.">}}

Data is reformatted by mCerebrum applications to a common data point abstraction to support the wide variability in current and future data sources.
mCerebrum supports a variety of external and internal sensors including:

1. Electrocardiogram (ECG)
2. Respiration
3. Accelerometers
4. Gyroscopes
5. Magnetometers
6. Heart Rate
7. RR-Interval
8. Galvanic Skin Response (GSR)
9. Barometer
0. Location (GPS)
1. Ambient and UV Light
2. Ultra-wideband RF
3. Sound
4. Video

Self-report and EMA are represented as JSON documents.

#### Resilient Communication management
Sensor devices operate either in _batch_ or _streaming_ mode, with some supporting both, and the associated challenges differ.  Devices sending only biomarkers (e.g., Fitbit trackers) to a smartphone usually operate in batch-mode, where the smartphone needs to connect frequently enough to ensure that the necessary data or biomarkers are synced before any information is lost due to memory limitations. Devices collecting raw sensor data that require real-time processing on a smartphone for triggering notifications or interventions, are usually streamed continuously without local storage to compensate for battery depletion and is the scenario of usage considered here.

In such streaming scenarios, even a brief disconnection can result in lost data; thus, it is critical that streaming sensors be able to maintain a persistent connection to the phone.  For example, a smoking algorithm utilizes up to five seconds of wrist movement data to aid detection of smoking behaviors and if communication with the band were to fail, a critical event could be missed.

Radio disconnections between a streaming wearable and smartphone are another source of communication problem and may occur due to many reasons including the wearable and phone getting out of radio range due to physical separation, low battery, a user turning off the device, and radio frequency interference due to the environment or other devices in radio proximity.  mCerebrum utilizes a two-step approach to address disconnections. First, it attempts to auto reconnect with sensor devices utilizing a back-off mechanism where initially it retries every three seconds and incrementally slows to every 30 seconds after subsequent failures. Second, the user is notified that a particular device is not connected and supplied with guidelines such as to check the battery level, restart device, or reset the system to minimize data loss.

#### Handling Large Data Objects

Audio and video data are typically sampled at much higher rates than DataKit's 4.5 kHz limit. To allow collection and sharing of these two data types in DataKit, we consider two approaches to overcome Android's interprocess communication (IPC) limits. First, we split data into chunks and send individually to Datakit, where chunks are subsequently recombined, similar to the case of TCP packets. This approach requires 0.14 seconds to transfer 10 MB of binary data, sustaining 71 MBps of throughput.

Second, a secure file sharing approach between an application and DataKit allows sharing though _FileProvider_ which facilitates secure sharing of data by creating a `content://URI`, allowing a temporary grant of read and write access. DataKit can then directly access this file using the `URI`. This approach requires 0.11 seconds to transfer 10 MB of binary data at 90 MBps, resulting in slightly higher throughput and lower IPC load, making it a preferred mechanism for handling large data objects in DataKit.

#### Scalable Storage of High-Rate Sensor Data
SQLite is the de facto datastore layer on mobile devices including Android and iOS, but it is unsuitable for storing high-frequency raw sensor data streams. Such workloads, including our own, store data that is seldom deleted or updated (e.g., sensor samples), and are often small in (record) size e.g., a single message record could be a few hundred bytes, mCerebrum records 12 bytes, on average.

Writing data streams to SQLite can be prohibitively expensive due to SQLite database journaling and its update-in-place semantics i.e., records reside at a particular location in stable storage, and updates mutate the record directly. Furthermore, flash memory (the dominant stable storage medium in mobile devices) is page-oriented, which means that each record write corresponds to an entire read and write of a page[4]; common page sizes for NAND Flash memory chips today are around 8KB, which further increases write amplification

> Write amplification refers to the actual amount of data that is rewritten for a given record e.g., if records are stored in 8KB pages, then writing a 12 byte record results in writing at least an 8KB page.

for small records that many applications (including our own) exhibit. In general, a single record inserted into a table with $k$ indexes translates into $$2~\times~(k+1)$$ pages written under SQLite[4].

Consequently, when using SQLite to store raw sensor data, as data size grows, the query performance begins to degrade and fall behind the rate necessary for real-time computation of biomarkers. After about 8 hours of data collection, biomarker computations begin to timeout due to growing query response time.

Log-structured storage systems under development, such as RocksDB[5], may provide an alternative to SQLite; however, RocksDB aims to support general RDBMS workloads and lacks data sync capabilities between the mobile device and the cloud platform, which is a key requirement in mCerebrum.

To address the specific requirements of mobile sensor data workloads, we have developed a custom log-structured storage layer called _Pebbles_, which is optimized for high-frequency append-only writes of data arriving in batch or record streams. Pebbles also provides transparent data sync, allowing applications to offload data to the cloud for further processing and data archive. On the mobile device, data is stored in a circular log to maximize the throughput of flash memory. To support fast queries, Pebbles maintains a lightweight index on a logical timestamp and topic, which is used to identify data streams.


{{< figure src="/img/under-the-hood/mcerebrum/pebbles.png" title="Write performance" caption="Maximum write throughput of SQLite and Pebbles when varying the write size.">}}

This figure shows the max write throughput of Pebbles versus SQLite by varying data write sizes. This benchmark was performed on the internal flash memory of a Samsung Galaxy Tab S2. Each system was configured with an 8MB in-memory buffer and performed a total of 4GB writes. The optimal throughput of 72 MBps was determined by performing one large consecutive write to the internal memory.

At lower data write sizes, such as those exhibited by typical mCerebrum applications, Pebbles outperforms SQLite by more than 20x. The performance gain of Pebbles is directly related to the lower write amplification relative to SQLite. In the lower data write sizes, the CPU becomes the bottleneck, preventing Pebbles from saturating maximum storage bandwidth. Nevertheless, the achieved throughput is sufficient for mCerebrum.

At large data writes, such as those to be exhibited by the mCerebrum batch data workloads, Pebbles is able to saturate storage bandwidth and outperforms SQLite by more than 4x. SQLite is not capable of saturating the storage bandwidth at these large write sizes due to system overhead, including primary key constraints and index maintenance, which attribute to increased write amplification. In Pebbles, write amplification is minimized through the use of a circular log that is clustered with the primary index i.e., both are append-only on new data writes and garbage collection is performed, on both, sequentially with an optional cloud data sync.



## Analyze: Concurrent Computation of Multi-Sensor biomarkers
The second tenet, _analyze_, is principally responsible for processing the collected high-rate sensor data to compute features and biomarkers that can be used by multiple apps throughout the whole system. The main challenge is to screen the data for acceptable quality, clean the data, compute hundreds of features, and then apply the machine-learning models of all biomarkers, all in real-time, without falling behind the incoming data rate and without saturating the CPU and memory of resource constrained phones. One key approach to making this feasible is to facilitate efficient sharing of intermediate results (e.g., features) so computation can be reused.

We first describe in the [data and computation reuse]({{< relref "#data-and-computation-reuse" >}}) section how data and computation can be reused to scale the analytics. Next, [handling system overload]({{< relref "#handling-system-overload" >}}) explores and evaluates the techniques to manage system overload so as to manage Android's quality of service system to support continuous high-frequency sensor data analysis. Finally, [real-time computation and sharing of features and biomarkers]({{< relref "#stream-processor-real-time-computation-and-sharing-of-features-and-biomarkers" >}}) describes Stream Processor that implements real-time computation and sharing of features and biomarkers throughout mCerebrum. We also analyze the impact of such sharing on improving CPU and memory efficiency.

### Data and Computation Reuse
It is not enough to have communication efficiency in each app, the system needs to reuse as much data and computation as possible.  The modularization of mCerebrum allows sensor data to be collected once by a single application where it is published through DataKit for the rest of the system to receive.  This allows multiple applications to receive data concurrently by subscribing to data streams. Computation reuse occurs when various processing components of the platform compute intermediate results or resulting biomarkers that are placed on the DataKit bus where others can utilize these processed streams instead of recomputing from raw data.

#### Supporting Onboard Sense-Analyze-Act
To enable the entire pipeline of sense-analyze-act locally on the phone, mCerebrum supports three different styles of data processing: micro-batch, batch, and on-demand. In each of these instances, the computation must not fall behind data arrival rate, i.e., meet a real-time constraint. Streaming operations, such as data quality or visualization, need to receive data from the system and process it almost immediately; they use a micro-batch latency of one second. On-demand computations or batch processing, such as biomarker computation, require the data be queried in blocks from DataKit. In our current implementation, for the purposes of computing various biomarkers such as stress and smoking, we use a batch latency of 60 seconds.

Due to high load, computational complexity is a concern for all data processing operations within mCerebrum.  When possible, computationally efficient algorithms are preferred such as online algorithms, i.e. mean and variance. For computationally expensive operations such as computing percentiles, the algorithms are replaced with online approximations. In the case of convolution, the amount of data to be processed is limited to control CPU load.

### Handling System Overload

The Android operating system is based on the Linux kernel and applications are run as self-contained processes.  This allows Android to manage the Quality-of-Service (QoS) it provides to the user; however, this QoS is designed for regular consumer use and not configurable for long-running background applications such as the ones we utilize to provide a continuously running pipeline of sense-analyze-act.  Android selectively kills, and subsequently removes from memory, applications as the system begins to run out of resources.

To determine which processes should be killed when low on memory, Android places each process into an importance hierarchy based on the components running in them and the state of those components. The process types are (in order of importance): _foreground_, _visible_, _service_, and _cached_.
Due to the QoS constraints from the OS, we find that our applications are the typical ones removed due to their _service_ process state and worse, the OS sends a `SIGNAL_KILL` command instead of a signal that can be trapped by our applications for a graceful shutdown.  This forces our applications to have a second watchdog application that can restart an application if the OS decided to remove it.

mCerebrum adopts three separate mechanisms to combat the overload introduced and subsequent semi-random application closing.  First, the core service in critical applications is declared as a _foreground process_, which is a way to request that the OS not remove this application from a running state.  This is especially critical for applications that interact with the participant through a user interface or a scheduling algorithm.  Second, the mCerebrum kernel acts like a watchdog system for the rest of the application services.  It periodically checks (every 30 seconds) to ensure that the list of services it expects to be running are operational.  In the event that a service is not functional, it utilizes an exponential back-off mechanism to quickly restart a service and in the event of continued failure, it will slow attempts to restart processes.  Finally, every service must maintain a persistent copy of internal state on the internal phone memory and be able to resume when restarted. In addition, we adopt several optimizations (described below) to limit system overload and avoid application removal by the OS.

#### Micro-batching to Control Communication Load
Sharing and processing data as they arrive in real-time increases both the system and communication load due to the maximum bandwidth and maximum buffer size limits for Inter-Process Communication (IPC) that are used to share data and intermediate results among the data sources and requesting applications.

{{< figure src="/img/under-the-hood/mcerebrum/freq_cpu_new.png" title="Micro-batch systems evaluation" caption="The effect of micro-batch latency on DataKit's communication bandwidth and CPU usage. We observe that with no latency, communication bandwidth is limited by bandwidth limits of IPC, while at higher latency, bandwidth is limited by the buffer size limits of IPC.">}}

Our initial implementation serialized measurements from sensors into individual messages before sending them through DataKit; however, once the data rate exceeded 150 hertz (on a Samsung S4), the system queues overflowed and the system began losing data. We adopt a micro-batching design where data is shared for computation in small batches that introduces a small latency, but significantly reduces system overload.

This figure shows the effects of various choices of micro-batching latency on the frequency of data the system can process and the CPU cost associated with it. We note that the IPC communication buffer size is limited to 1 MB. While introducing micro-batching helps reduce system load, it affects applications that need real-time data. Among them, the most delay sensitive is the Plotter for visualizing sensor data such as ECG, accelerometers, and gyroscopes. We choose a latency of one second that provides a bandwidth of 450 hertz for a CPU load of 17 percent. There is a noticeable delay in rendering the plots of sensor data in visualization, but it is acceptable for most purposes.

#### Effects of Buffer Size on System Load

{{< figure src="/img/under-the-hood/mcerebrum/table_batch_size.png" title="Effect on CPU utilization" caption="Measurements (seconds) normalized to  60 second iterations for CPU time decrease as the buffer size is increased from 30 to 300 seconds.  0.34 seconds (17%) can be saved through buffering; however, it comes with an increase in memory load (156%). ">}}

This figure illustrates the trade-off between buffering data and the computational and memory loads on the system.  This experiment runs our biomarker computation pipeline and varies the amount of data buffered between 30 and 300 seconds. The memory status of the smart phone is recorded by executing `adb shell dumpsys meminfo` command at two hertz. Applications also logged the starting time and computation time of each iteration. We ran each experiment for 20 minutes and the mean computation time and mean memory usage are computed. Complex biomarkers such as stress, smoking or eating, benefit from the additional buffer size which allows them to produce more accurate results; however, this comes at the expense of memory utilization. A biomarker's utility can be a function of it's temporal locality to the measuring event, such as the case with stress, where a five minute delay places any potential intervention outside of the episode, thereby reducing overall effectiveness. Additionally, buffering too much data increases the computational time and resources needed thus resulting in Android stopping certain data collection and processing application rendering the this platform unusable.  Computations on large buffer sizes effectively cause a CPU utilization spike which is interpreted by Android as a resource demanding application, and the application becomes a candidate for shutting down.

We currently use an operating point of one minute that provides acceptable latency while limiting system overload. Improvements in the computational model and hardware profile of the phone will change these operating points. Dynamic selection of the best operating points given a biomarker model and hardware profile is a subject of future work.


### Stream Processor: Real-time Computation and Sharing of Features and Biomarkers

The majority of high-frequency signal processing occurs under the _Stream Processor_ framework, which is designed to support real-time computation and sharing of features and biomarkers. It mirrors the data structure from mCerebrum and provides appropriate buffering and estimators for several windows-based signal processing pipelines.

_Stream Processor_ includes a number of design trade-offs that improve processing performance or constrain resource utilization so as not to adversely affect mCerebrum's system performance.  First, data is processed with a _batching_ mechanism where all algorithm pipelines receive data every 60 seconds as a way to allow the smartphone CPU to operate in burst mode for better energy efficiency and to limit the amount of reprocessing of data that must occur if a sliding window or smaller windows were to be utilized.  Second, data is kept in RAM only for the current window of computation unless the developer explicitly configures historic state preservation.

Third, algorithms are usually implemented as pipelines since they gain significant computation reuse by sharing originating sensor sources.  For example, both stress[6,7], an algorithm designed to compute physiological arousal from ECG and respiration to estimate stressful episodes, and smoking[8], combines respiration and wrist motion information to determine when a cigarette puff occurs, share common respiration features and the smoking algorithm takes advantage of existing computation and augments the processing with its new features.

Stream Processor is also responsible for generating a feature vector from the various computed data streams and evaluating a learned model for biomarker generation that is trained from existing annotated data sets.  These models are currently based on a support vector machine (SVM); however, any model that is efficiently evaluated is capable of being run.

Despite efficient design, 14.87 &plusmn; 4.12 seconds each minute on average is spent running the signal processing algorithms and results in a 13 percent reduction in total expected system lifetime. This will only grow as more biomarkers are included for real-time local computation. Future work is needed to investigate methods to limit CPU load, e.g., explore cloud offloads for biomarker computation from raw sensor data.

### Quantifying the Benefits of Computation Reuse --- A Case Study

{{< figure src="/img/under-the-hood/mcerebrum/Venn.png" title="Shared Computation Overview" caption="Features are shared among various biomarker computation algorithms, allowing for computation reuse.">}}

To analyze the effect of computation reuse, we created a single app for detecting smoking, stress, activity, and eating, and additional apps isolating the individual biomarker computations. The applications were run simultaneously to measure CPU and memory load and once again with computation sharing enabled. This figure shows the features that are shared among these four biomarker computations. For example, respiration data is used for both smoking detection and stress detection, allowing preprocessing and many feature calculations to be shared resulting in lower CPU and memory utilization.

{{< figure src="/img/under-the-hood/mcerebrum/time_mem.png" title="Shared Computation" caption="The effects of computation reuse on CPU and memory efficiency.  The first columns show the CPU time and memory usage when computing four biomarkers, Smoking, Stress, Eating, and Activity, independently without sharing computation between the algorithms. For this example, a reduction of 27% CPU time and 47% memory is achieved through this reuse, as shown in the second columns.">}}

This figure shows a 27 percent reduction in CPU time and 47 percent reduction in memory achieved by computation reuse.


## Act: Burden- and Context-Aware Interactions with participants


The final tenet of our platform, _act_, combines both _sense_ and _analyze_ outputs to engage with a participant during his/her study period. Together with sensor data, direct inputs from participants are also collected in research studies. Participant interaction is generally grouped into three categories: _voluntary_, _prompted_, and _glanceable_. Voluntary inputs can be provided through self-report buttons. Prompted interactions allow the system to obtain information from a participant through an EMA mechanism or to provide an intervention (EMI). Prompts are also generated to ask participants to collect episodic data from some devices or to remind them to take medications. Finally, glanceable interactions are implemented by updating the graphical user interface. For example, real-time data quality assessment is displayed on the home screen.
Of these, prompted inputs and interventions represent interruptions to the participant and hence must be carefully coordinated to limit user burden.

There are several new challenges in the design of scheduling EMA and EMI prompts in research studies collecting both streaming sensor data with sense-analyze-act capability and EMAs and EMIs. First, prompts should be coordinated from all sources, including those generated by biomarkers, to limit burden on participants while satisfying all study requirements. This includes using sensor-inferred contexts and deliver prompts or interventions only when the participant is available. The second challenge is to incorporate sensor data quality in prompt generation so that good quality sensor data is available preceding self-reports. In the following, we describe [study requirements]({{< relref "#ema-emi-scheduling-requirements" >}}) and our design of [participant interaction manager that is both burden- and context-aware]({{< relref "#burden-and-context-aware-ema-emi-scheduling" >}}).


### EMA/EMI Scheduling Requirements

Ecological Momentary Assessments (EMAs) are a cornerstone for biomedical studies because of their ability to obtain a participant response in the moment. They can be prompted randomly (to obtain unbiased daily estimates), based on time of day (to ensure coverage), based on self-reported events (to obtain context surrounding a self-reported event such as smoking lapse), and now also based on events detected by sensors (e.g., elevated stress). In addition, participants can also be prompted to engage in an intervention (e.g., stress relaxation), to collect episodic data from devices (e.g., blood pressure), and to remind them to take medications. Each prompt involves its specific constraints and irrespective of the source, each prompt represents an interruption and burden on the participant.

Each study has a unique protocol (i.e., usually part of their innovation), requiring the EMA scheduler to work in conjunction with study-specific configuration that implements the rules of the study protocol. Studies may involve:

1. scheduled assessments, such as the beginning of the day, the end of the day, or at specific times,
2. random assessment, where the time of this assessment is randomly generated within a specified window,
3. in response to self-reported events, and
4. event-triggered assessment (e.g., in response to smoking or stress).

Second, the EMA scheduler needs to support conditional operations based on computed data streams. Some of the conditions include:

1. driving status, to ensure that an EMA is not delivered to a person in a moving vehicle,
2. data quality, allows the system to verify that the sensors are worn properly before generating the assessment (to ensure labels and sensor data are both available together), and
3. battery level, to ensure that assessments are happening either with sufficient battery or as a way to prompt a participant to charge a particular piece of the system.

Third, the last EMA or EMI triggering time can be used to ensure that subsequent prompting or interventions do not occur in close proximity to each other. Fourth, the total number of prompts triggered are limited to a maximum (in each time block) to constrain the user burden according to study protocol rules. Fifth, the day may be divided into time blocks with minimum number of EMA's in each block to ensure sufficient temporal distribution of EMA's. Sixth, no prompts are to be delivered if privacy controls are exercised to suspend prompts. Finally, start and end of day can be provided so that no prompts will occur before or after these times.

### Burden- and Context-aware EMA/EMI Scheduling

{{< figure src="/img/under-the-hood/mcerebrum/Bipartite.png" title="EMA/EMI Scheduler" caption="A bipartite graph design of EMA/EMI scheduler. Boxes on left side show the inputs to the actions/controllers on the right, which prompt the participants. Feedback is accomplished by examining the conditions surrounding the participant response and passed back to key input blocks.">}}

mCerebrum uses a bipartite-graph design that fulfills all of the above requirements and is thus able to satisfy the requirements of all [ten studies](/deployments).
In addition, our design supports dynamic adaptation to use the user response (or lack of) to meet study requirements with gradual relaxation of constraints through a feedback loop.

The inputs column (left-side) enumerates many current choices available in mCerebrum and include: burden constraints, random and event-triggered inputs, restrictions on actions through privacy constraints, start and end of day, and various time operations, user context, and data quality and battery assessments. These inputs can be mapped in arbitrary ways to a set of actions or controllers (right-side) and is defined as constraints across multiple applications as part of a study protocol. Ultimately, the output of an action or controller results in feedback information being incorporated back into the input side. These feedback loops allow mCerebrum to adapt to changing burden, personal preferences, or to gradually escalate the prompting to become more aggressive in requesting an action from a participant (to meet study requirements).

For random and time based assessments, the EMA scheduler estimates the time of when it should be triggered. Due to the dynamic nature of self-reported event and event-triggered assessment, the EMA scheduler schedules it preemptively based on their appearance. There might be a case when multiple assessments may appear at the same time. To handle this issue, the EMA scheduler takes each of these events one by one as in a FIFO queue and checks all of the constraints for this event and deliver the EMA. After completion of an EMA, it returns back to process the next event. This approach also ensures that multiple EMAs are not triggered simultaneously. For random assessments, if it fails to deliver due to the constraints or conflicts with another assessment, it is rescheduled. Before delivering the EMA, the EMA scheduler checks constraints and if all constraints are successfully passed, the user is notified to the availability of an EMA assessment and the response is then used to the measure burden and constraints. In several studies, the EMA/EMI scheduler attempts an average of 55 prompt deliveries per day with an average processing time of 0.18 seconds each, negligible when compared to the CPU execution time of a stress or smoking biomarker.



## Conclusion
Interest and activity in developing new biomarkers and interventions from mobile sensor data is rapidly expanding. But, assembling a reliable software platform to support the collection of raw sensor data from a wide variety of sensors combined with the real-time computation of biomarkers on the phone to trigger notification and intervention requires significant time, effort, resource, and multidisciplinary experience. This paper presents an end-to-end system, consisting of 23 applications, that has evolved from rich experiences over the last half a decade. It is being adopted in multiple concurrent field studies and is now openly available for the community to use and grow as an open-source platform. With growing adoption and convergence on a common platform, native support in the commercial devices and operating systems may grow, making it easier to use and more efficient to run on participants' personal phones. This may further accelerate data science and health research by allowing reuse of code and models among the community.

---

1. Google’s FIT. 2017. Online at https://www.google.com/. visited April (2017).
2. Denzil Ferreira, Vassilis Kostakos, and Anind K Dey. 2015. AWARE: mobile context instrumentation framework. Frontiers in ICT 2 (2015), 6.
3. Apple’s HealthKit. 2017. Online at https://developer.apple.com/healthkit/. visited April (2017).
4. Gihwan Oh, Sangchul Kim, Sang-Won Lee, and Bongki Moon. 2015. SQLite Optimization with Phase Change Memory for Mobile Applications. Proc. VLDB Endow. 8, 12 (Aug. 2015), 1454–1465. DOI:https://doi.org/10.14778/2824032.2824044
5. RocksDB. 2017. Online at http://rocksdb.org/. visited April (2017).
6. Karen Hovsepian, Mustafa al’Absi, Emre Ertin, Thomas Kamarck, Motohiro Nakajima, and Santosh Kumar. 2015. cStress: towards a gold standard for continuous stress assessment in the mobile environment. In Proceedings of the 2015 ACM International Joint Conference on Pervasive and Ubiquitous Computing. ACM, 493–504.
7. Hillol Sarker, Matthew Tyburski, Md Mahbubur Rahman, Karen Hovsepian, Moushumi Sharmin, David H Epstein, Kenzie L Preston, C Debra Furr-Holden, Adam Milam, Inbal Nahum-Shani, and others. 2016. Finding Significant Stress Episodes in a Discontinuous Time Series of Rapidly Varying Mobile Sensor Data. In Proceedings of the 2016 CHI Conference on Human Factors in Computing Systems. ACM, 4489–4501.
8. Nazir Saleheen, Amin Ahsan Ali, Syed Monowar Hossain, Hillol Sarker, Soujanya Chatterjee, Benjamin Marlin, Emre Ertin, Mustafa al’Absi, and Santosh Kumar. 2015. puffMarker: A multi-sensor approach for pinpointing the timing of  rst lapse in smoking cessation. In Proceedings of the 2015 ACM International Joint Conference on Pervasive and Ubiquitous Computing. ACM, 999–1010.
