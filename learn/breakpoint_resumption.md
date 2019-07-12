# Breakpoint Resumption

EnOS™ Edge supports breakpoint resumption. If the communication between the Edge and the cloud is interrupted, the Edge can continue to collect data from sub-devices and cache it locally. The data cached locally will be transmitted again once the network connection is restored.

The dual-way message confirmation mechanism for Edge and cloud ensures that the data cached in the Edge must be sent to the cloud, ensuring data integrity in case of network interruption.

The cache size can be calculated based on the following factors:
- Number of measuring points
- Data types 
- Sampling periods
- Time-to-live period for cached data and 
- Storage size

The daily cache size per sub-device can be calculated as follows:

Daily data volume = (total measuring points × measuring point size (byte)) × (24h × 3600s/h ÷ sampling period (s))

Where the measuring point size can be defined as approximately 25 bytes.

## Example

Assume that there are 100 devices, each sub-device has 50 points, each point and its related attributes occupy 25 bytes, the sampling period of the point is 5 seconds, and the data are continuously collected for 24 hours a day. Assume that a 64GB hard drive is selected;

Then the amount of data one day per device is: 50 × 25 × 24 × 3600 ÷ 5 = 21,600,000 bytes. So the total cached data for 100 devices in Megabyte (MB) is 21,600,000 × 100 ÷1024 ÷ 1024  ≈ 2060 MB

For the 64GB hard disk itself, space must be reserved for system, virtual memory space, and other required space. Assume that 40GB can be guaranteed for local storage;

It can store 40 × 1024 ÷ 2060 = 20 days of data.


.. note:: Excessively large data cache might cause issues in breakpoint resumption. Reserve a maximum of 4GB space for cache.
