# Data resolution

The resolution of data ingested via the EnOS Edge is determined by the
following frequency data:

- Data sampling frequency between the Edge and devices

  This frequency is defined in the communication protocol configuration file, which determines the raw data resolution and accuracy.

- Data transferrring frequency between the Edge and the cloud

  This frequency is defined in the device model. There are three data uploading modes:

  - Real-time: The data uploading frequency is the same with data ingestion frequency in the protocol. That is, ingested data will be uploaded to the cloud immediately. With this mode, the resolution of final data stored in the cloud is the same with the raw data collected in the communication level.

  - Timer: Ingested data will be uploaded to the cloud by the frequency defined in the device model.

  - Change: Ingested data will be checked in the Edge and will be uploaded once the data value changes.
