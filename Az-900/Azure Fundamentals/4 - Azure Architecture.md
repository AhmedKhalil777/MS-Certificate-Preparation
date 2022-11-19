# Azure Building Blocks
- Regions (Bad Regions !! + Terible of Azure Names of Regions)
- Avilibility zones
- Resource groups
- Azure Resource Manager

## Regions & Aviliability Zones
- They have a great impact of the performance 
- A region is a set of near by data centers, Latency defined Perimeter, 
  - Latency is the time it takes data to travel.
  - Also means that data centers are not "too far" from each other.

> Choose the region based on 
    - The Locations of your customers
    - Features are limited to some regions
    - Price


### Paired Regions
- Each region is paired
- Paired within same geographic area except Brazil South
- Outage Failure => If the primary region has an outage you can failover to the secondry region.
- Used for replications 
- Only one region in a pair is updated at any one time

### Aviliability Zones
- _Physicl Location_ Each availiability zone is a physical location within a region
- _Independent_ Each zone has its own power , cooling , networking
- _Region has min 3 Zones_
- So when you update a resource found in zone 1 it updated in zone 2



## Resource groups & Azure Resource Manager
- A resource group is a collection of resources
- A resource must exist on a single group
- Remove or add any resource to a group is availiable
- Move is aviliable
- _Multible Regions_ resources from multible regions can be in one group
- _Access Control_ You can give users Access control to a resource group and everything in it
- _Interact_ A resource can interact with other resources from different groups
- _location_ a resource group needs a location, as it stores meta data about the resources in it.


### ARM Azure Resource Manager

- ARM is the Key tool to manage resources, is the processor unit that takes request from (Portal , CLI, Powershell, SDKs) and Process them to resorces

#### Benefits
- You can manage , deploy , monitor resources as a group
- _Consistency_ Deploying resources goes throw this point so from any tool will create the same processing __Consistent State__
- _Dependencies_, Define dependencies between resources to make sure they don't get in a fight
- Access Control 
- Tagging - assign a label to resource
- Billing 


