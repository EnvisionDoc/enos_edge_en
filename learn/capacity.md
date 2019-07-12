# Data Access Capacity

The EnOS™ Edge acts as the data collector for the EnOS™. Its performance is represented in the number and sampling frequency of measuring points supported. The performance of the Edge is subject to the following hardware and software configurations:
- Sampling frequency as defined by protoco
- Frequency defined in the device model
- Number of connected sub-devices
- Number of measuring points
- Server CPU
- Memory
- Hardware type.

Therefore, it is difficult to accurately specify the number of measuring points that an Edge can support. Based on the internal performance test results, the following examples are given for reference. You may contact the Envision Technical Support Team to learn about the detailed capability of Edge in your scenario.

.. list-table:: Table: Reference for the Number of Accessible Measurepoints Supported by EnOS™ Edge
   :widths: auto

   * - Hardware configuration
     - Instructions for measurepoint sampling frequency
     - Recommended number of measuring points
   * - Linux OS / 4-Core CPU / 8Gb Memory
     - AI, every 10 or a multiple of 10 second, 42%
       AI, every 1 to 9 seconds, 1%
       DI, sampling upon change, 57%
     - 20000

<!--end-->
