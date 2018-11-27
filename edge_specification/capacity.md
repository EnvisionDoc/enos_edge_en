# Capacity

The data ingestion capacity of EnOS Edge can be evaluated by the supported amount of domain points and data sampling frequency. However, various impacting factors, including sampling frequency defined in
protocols and device models, device amount, hardware configuration, etc., can affect this capability.

Therefore, it is difficult to provide an accurate number of domain points supported by the Edge. Based on internal testing results, the following data is provided for reference.

*Table: Amount of supported domain points by EnOS Edge*


<table>
  <tr>
    <td>Hardware Configuration</td>
    <td>Data type/mode/sampling   cycle level/Percentage</td>
    <td>Domain points</td>
  </tr>
  <tr>
    <td>Linux OS / 4 Core CPU /   8G Memory</td>
    <td>AI/Timer/10second   sampling level-42%<br>
      AI/Timer/second level -1%<br>
      DI/Change/../-57%</td>
    <td>20000</td>
  </tr>
</table>
