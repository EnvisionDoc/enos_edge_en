# Typical Deployment Mode

EnOS™ Edge supports the following deployment modes:

## Deployment mode 1

Edge communicates via a VPN link with cloud through a firewall, and connects to a third-party system or sub-devices via Ethernet.

.. image:: ../media/image002.png
   :alt: Figure: Deployment Mode 1

## Deployment mode 2

Edge is deployed in a light-weight, wireless hardware product (such as Dell 3002), and communicates directly with the cloud over a 3G/4G network while connects toa third-party system or sub-devices via Ethernet.

.. image:: ../media/image003.png
   :alt: Figure: Deployment Mode 2


## Deployment mode 3

Two Edges are deployed across an air gap. Edge 1 inside the air gap is connected to a third-party system or sub-devices via Ethernet, and then forwards the data to Edge 2 across the gap using a specific protocol. Edge 2 communicates with the cloud via a VPN link established through the firewall and then to the cloud.

.. image:: ../media/image004.png
   :alt: Figure: Deployment Mode 3
   

<!--end-->
