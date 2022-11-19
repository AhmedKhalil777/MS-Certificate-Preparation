# Virtual Network (VNet)

> Enables the resources to securely communicate with each other and the Internet and the on-premises networks 

- The Network is virtual so _you don't have any access to the hardware_ (Hardeware is hidden away => Abstracted)


- VNet belongs to a single region, Every resource on the VNet must be  in the same region too

- Belongs to one subscription, but subscriptions can have multiple VNets 


## Adventages 
- Scaling => Adding more VNets or more Addresses to one is more simple.
- Aviliabilty => Ensures high aviliabilty to resources (Peering VNets) using a Load Balancer or a VPN Gateway 
- Isolate => manage and organize resources with subnets and network security group

## Virtual Network Concepts

- __Address Space__ 


### Address Space 
> is a range of Ip Addresses <...> eg. <192.168.0.1-192.168.0.252> that are aviliable,
- now each resource can get its own IP Address
- the resources in the same Address space can find each other and communicate
- The Address space is assigned to one VNet

### Subnet
> Enables you to segment the VNet into one or more sub network and enable to allocate portions of the Address Space to each new subnet

- _Resource Groping_ the resource group onto the the same subnet to make it easier to work together and to keep an overview
- _Address Allocation_ Much easy now to allocate Ip Address to a resource for a group
- _Subnet Security_ Use network security groups to secure individual subnets 

### VNet Peering
> Connecting Multi VNets with each other with Microsoft Backbone network
- Low Latency - High bandwidth
- Link Separate networks
- Data Transfer easily between subscriptions and deployment models in separate regions