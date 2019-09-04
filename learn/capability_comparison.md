# Capability Comparison Between Edge Product Series

The following Edge series are provided, each with different capabiliy sets, designed for different scenarios and requirements.

## Specifications Comparison

The following table shows the specifications of different Edge series.

.. csv-table:: Edge Product Series
      :header: "Product Series", "Position", "Senario", "Feature"
      :widths: auto

      "Edge Gateway Logger", "Light-weight gateway or data logger", "Distributed solar, building storage, industrial parks, commercial buildings, smart cities, and other light-weight edge computing scenarios", "ARM-based, cost-effective"
      "Edge Gateway", "Gateway from small to large scale", "Centralized socar and wind, large-scale park and other related scenarios, large-scale data transceiver and light-weight edge computing", "X86-based, high performance"
      "Edge Gateway STD", "Gateway and local platform to run local applications", "Gateway scenarios and local applications such as SCADA, alarm, reporting, Enlight, etc", "X86-based, designed with services and APIs, able to run applications"
      "Edge Extensive", "Regional small data center and for distributed deployment", "Regional small data center with monitoring and control, data analytics with Enlight, etc", "X86-based, designed to run applications, for distributed deployment"

## Function Comparison

The following table shows what functions different Edge series are capable of.

In the table, "Yes" indicates this function can run on all hardware of the Edge product. "No" indicates no hardware of this Edge device can support this function. "Partial" indicates the function can only run on some hardware instances of this Edge device.

.. csv-table:: Edge Function Comparison
   :header: "Function", "Edge Gateway Logger", "Edge Gateway", "Edge Gateway STD", "Edge Extensive"
   :widths: auto

   "Remote configuration", "Yes", "Yes", "Yes", "Yes"
   "Protocol conversion", "Yes", "Yes", "Yes", "Yes"
   "Data gap refill", "Yes", "Yes", "Yes", "Yes"
   "Edge computing formula and script", "Yes", "Yes", "Yes", "Yes"
   "Edge computing streamsets", "No", "Partial", "Yes", "Yes"
   "Data forwarding", "Yes", "Yes", "Yes", "Yes"
   "OTA", "Yes", "No", "No", "No"
   "HA", "No", "Yes", "Yes", "Yes"
   "Data service", "No", "No", "Yes", "Yes"
   "Model and asset service", "No", "No", "Yes", "Yes"
   "Alarm engine", "No", "No", "Yes", "Yes"
   "API service", "No", "No", "Yes", "Yes"
   "Application management", "No", "No", "Yes", "Yes"
   "IAM and app portal", "No", "No", "Yes", "Yes"
   "TSDB", "No", "Partial", "Yes", "Yes"

<!--The end-->