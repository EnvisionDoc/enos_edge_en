# Typical Deployment Model

There are three typical deployment models for EnOS Edge.

## Deployment Model 1

Edge connects to EnOS Cloud via the VPN tunnel created from the on-site network gateway. On the other side, the Edge connects to devices or third party systems via the Ethernet network.


.. image:: ../media/image002.png
   :alt: Figure: Deployment model 1


## Deployment Model 2

The Edge application is deployed in light-weight wireless hardware such as Dell 3002, then connects to EnOS Cloud via 3G/4G network. On the other side, the Edge connects to devices or third party systems via the Ethernet network.


.. image:: ../media/image003.png
   :alt: Figure: Deployment model 2


## Deployment Model 3

The Edge is deployed with gatekeepers such as Nari Syskeeper. An Edge device is deployed separately inside and outside of the gatekeeper, with the inside one named Edge-1, and the outside one named Edge-2. Edge-1 connects to devices via the Ethernet network and then transfers data to Edge-2 through the gatekeeper private protocol. Edge-2 connects to the EnOS Cloud via the VPN tunnel created to the on-site gateway to the EnOS Cloud.


.. image:: ../media/image004.png
   :alt: Figure: Deployment model 3

<!--end-->
