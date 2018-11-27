# Breakpoint resumption

EnOS Edge supports breakpoint data transfer resumption. When the internet connection between the on-site edge and the cloud breaks down, the Edge continues to ingest device data and stores data locally. When the connection recovers, it resumes transferring the historical data to the cloud.

There is a bi-directional message acknowledgement mechanism between the Edge and the cloud, which ensures that all the ingested data are sent to the cloud. In this way, the integrity and unanimity of the data can be effectively guaranteed in case of network break.

The size of hardware storage required for breakpoint resumption can be
calculated by the amount of domain points, data type, data sampling
frequency, and time needs for local storage. The data size for one-day
storage can be estimated by the formula below:

$$1\ day\ data\ (bytes) = (total\ domain\ points \times 25) \times (24h \times 3600s/h \div sampling\ frequency(s))$$

An estimation example：

Suppose that there are 100 devices, each device contains 50 domain
points, the size of each point and its attributes is 25 bytes, the
sampling frequency is 5s (24 hours continuous sampling), and a 64GB
hardware drive is selected. Then the data amount for 1 day is estimated
as below:

$$100 \times 50 \times 25 \times 24 \times 3600 \div 5 \div 1024 \div 1024 \approx 2060MB$$

To deduct system space, virtual memory space, and other reserved space,
suppose there are 40GB disk space left, then the edge can store
$40 \times 1024 \div 2060 \approx 20\ days$ of data.
