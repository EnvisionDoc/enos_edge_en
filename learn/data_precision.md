# Data Precision

The precision of the data transmitted to the EnOS™ through Edge is subject to the following factors:

1. Sampling frequency of device data

   This sampling frequency is configured in the protocol, and determines the precision of data transmitted to Edge.

2. Transmission frequency from Edge to cloud

   You can define the transmission frequency in **EnOS Edge > Template**. The **Upload Interval** field in the template details controls the frequency. Edge supports the following mode, or **Upload Type** as is in the console, for data transmittion between an Edge and the cloud:

   <!--Add a screenshot showing where "Upload Interval" and "Upload Type" are.-->

   - REALTIME: Edge directly transfers data to the cloud once it receives data from its sub-devices. The final precision of the data uploaded to the cloud is consistent with that of the data collected by Edge.

   - TIMER: Edge periodically uploads data to the cloud according to the upload interval you defined in the template. If the upload interval is 1,000,000 milliseconds, Edge would send the data to the cloud every 1,000,000 milliseconds. No data would be uploaded if Edge has not received any data within a time interval.

   - CHANGE: Edge checks received data. If any point value has changed from the last Edge checked uploaded data, it sends the updated value to the cloud. This mode applies to DI.

The data precision in the cloud is determined by the transmission frequency from Edge to cloud. The sampling frequency of device data determines the precision of the raw data. You will receive duplicate reports of data if the transmission frequency is higher than the sampling frequency.
