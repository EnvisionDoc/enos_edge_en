# Typical Deployment Mode

EnOS™ Edge supports the following deployment modes:

## Deployment mode 1

### Description

Edge communicates via a VPN link with cloud through a firewall, and connects to a third-party system or sub-devices via Ethernet.

### Scenarios

Applies to scenarios with high security and stability requirements.

.. image:: ../media/fire_walling.png
   :alt: Figure: Deployment with Fire Wall

## Deployment mode 2

### Description

Edge is deployed in a light-weight, wireless hardware product (such as Dell 3002), and communicates directly with the cloud over a 3G/4G network while connects to a third-party system or sub-devices via Ethernet.

### Scenarios

Applies to scenarios with low security requirements, such as connecting photovoltaic power plants in a industry park to EnOS.

.. image:: ../media/direct_connection.png
   :alt: Figure: Direct Connection


## Deployment mode 3

### Description

Two Edges are deployed across an air gap. Edge 1 inside the air gap is connected to a third-party system or sub-devices via Ethernet, and then forwards the data to Edge 2 across the gap using a specific protocol. Edge 2 communicates with the cloud via a VPN link established through the firewall and then to the cloud.

### Scenarios

Applies to scenarios with high security requirements, such as connecting concentrated wind farm, concentrated photovoltaic power plants, and electrical sub-stations.

.. image:: ../media/air_gapping.png
   :alt: Figure: Deployment with Air Gap
   

<!--end-->
