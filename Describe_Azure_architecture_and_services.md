# Describe Azure architecture and services

## Geographies, Regions & Availability Zones

### What is a Data Center?

- Physical Facility
- Hosting for groups of networked servers

### Azure Infrastructure

#### Regions

- Main Regions
  - West US
  - East US
  - North Europe
  - Southeast Asia
  - Japan East
- Key Characteristics
  - Geographical area on the planet
  - One but usually more datacenters connected with low latency network (<2 milliseconds)
  - Location for your services
  - Some services are available only in certain regions
  - Some services are _global services_, as such are not assigned/deployed in specific region (E.g. Traffic Manager for DNS routing, Azure Active Directory)
  - Globally available with 50+ regions
  - Special government regions (US DoD Central, US Gov Virginia, etc.)
  - Special partnered regions (China East, China North)
  - [Azure Latency Test](https://www.azurespeed.com/Azure/Latency)
  - [Azure Products availability by region](https://azure.microsoft.com/en-us/explore/global-infrastructure/products-by-region/)

#### Availability Zones

- Regional feature
- Grouping of physically separate facilities
- Designed to protect from data center failures
- If zone goes down others continue working
- Two service categories
  - Zonal services (Virtual Machines, Disks, etc.)
  - Zone redundant services (SQL, Storage, etc.)
- Not all regions are supported
- Supported region has 3 or more zones
- A zone is 1 or more data centers

#### Region Pairs

- Each region is paired with another region making it region pair
- Region pairs are static and cannot be chosen
- Each pair resides within the same geography
  - Exceptions is Brazil South
- Physical isolation with at least 300 miles distance (when possible)
- Planned updates across the pairs
- Data residency maintained for disaster recovery
- Examples
  **Region Pair A**|**Region Pair B**
  ---|---
  East US | West US
  UK West | UK South
  North Europe (Ireland) | West Europe (The Netherlands)
  East Asia (Hong Kong) | Southeast Asia (Singapore)

#### Geographies

- Discrete market
- Typically contains 2 or more regions
- Ensured data residency, sovereignty, resiliency, and complaince requirements are met
- Fault tolerant to protect from region wide failures
- Broken up into areas
  - Americas,
  - Europe,
  - Asia Pacific,
  - Middle East and Africa
- Each region belongs only to one Geography

## Resources, Resource Groups & Resource Manager

### Resources

- Generic object used to represent purchased services in Azure

#### Key Characteristics

- Objects used to manage services in Azure
- Represents service lifecycle
- Stored in a JSON Template, and contains:
  - Type
  - APIVersion
  - Name
  - Location
- Resource Group assignment is required when creating any resource

### Resource Group

- Logical container for all your resources

#### Key Characteristics

- Grouping of resources
- Holds logically related resources
- Organizing by
  - Type
  - Lifecycle (app, environment)
  - Department
  - Billing, Location or combination of those

#### Additional Information

- Each resource must be in one, and only one resource group
- Resource groups have their own location assigned (just stores metadata, does not impact resources)
- Resources in the resource groups can reside in different locations
- Resources can be moved between the resource groups
- Resource groups can't be nested
- Organize based on your organization needs but consider
  - Billing
  - Security and access management
  - Application Lifecycle

### Resource Manager

- Management Layer for all resources and resource groups
- Unified language
- Resources can be managed by user using:
  - Azure Portal
  - REST APIs
  - Powershell
  - CLI
  - SDKs
- Controls access and resources

## Azure Compute Services

Category of on-demand services used to run cloud-based applications

### Virtualization (Azure Virtual Machine)

- Emulation of physical machines
- Different virtual hardware configuration per machine/app
- Different operating system per machine/app
- Total separation of environments
  - file systems,
  - services,
  - ports,
  - middleware,
  - configuration
- Infrastructure-as-a-Service (IaaS)
- Total control over the operating system and the software
- Supports Microsoft marketplace and custom images
- Best suited for
  - Custom software requiring custom system configuration
  - Lift-and-Shift scenarios
- Can run any application/scenario
  - web apps & web services,
  - databases,
  - desktop applications,
  - jumpboxes,
  - gateways, etc.

### Virtual Machine Scale Sets (Azure Virtual Machine Scale Sets)

- Infrastructure-as-a-Service (IaaS)
- Set of identical virtual machines connected with a load balancer
- Built-in auto scaling features
- Designed for manual and auto-scaled workloads like web services, batch processing, etc.

### Containers

- Use host's operating system
- Emulate operating system (VMs emulate hardware)
- Lightweight (no OS)
  - Development Effort
  - Maintenance
  - Compute & storage requirements

#### Azure Container Instances

- Platform-as-a-Service (PaaS)
- Simplest and fastest way to run a container in Azure
- Serverless Containers
- Container groups contains containers
- Designed for
  - Small and simple web apps/services
  - Background jobs
  - Scheduled scripts

#### Aure Kubernetes Services (AKS)

- Platform-as-a-Service (PaaS)
- Open-source container orchestration platform
- Highly scalable and customizable
- Designed for high scale container deployments (anything really!)
- One container in one node (VM) - Multiple nodes connected to Load Balancer

### App Services

- Platform-as-a-Service (PaaS)
- Designed as enterprise grade web application service
- Supports multiple programming languages and containers

### Azure Functions (Function apps)

- Platform-as-a-Service (PaaS)
- Serverless
- Two hosting/pricing models
  - Consumption-based plan
  - Dedicated plan
- Designed for micro/nano services

### The Comparison

| Service             |     Config Control/Maintenance     | Autoscaling | Min Nodes | Max Nodes |            Scalability             |
| ------------------- | :--------------------------------: | :---------: | :-------: | :-------: | :--------------------------------: |
| Virtual Machines    | :star: :star: :star: :star: :star: |     No      |     1     |     1     |               :star:               |
| VM Scale Sets       | :star: :star: :star: :star: :star: |     Yes     |     1     | 1000/600  | :star: :star: :star: :star: :star: |
| Container Instances |        :star: :star: :star:        |     No      |     0     |    20     |           :star: :star:            |
| Kubernetes Service  |    :star: :star: :star: :star:     |     Yes     |     3     |    100    |    :star: :star: :star: :star:     |
| App Service         |           :star: :star:            |     Yes     |     1     |  20/100   |        :star: :star: :star:        |
| Functions           |               :star:               |     Yes     |     0     |    200    |    :star: :star: :star: :star:     |

### Summary

| Azure Compute Service | Type | Requirement                                                                                                |
| --------------------- | :--: | ---------------------------------------------------------------------------------------------------------- |
| Virtual Machines      | IaaS | Custom Software, custom requirements, very specialized, high degree of control                             |
| VM Scale Sets         | IaaS | Auto-scaled workloads for VMs                                                                              |
| Container Instances   | PaaS | Simple container hosting, easy to start                                                                    |
| Kubernetes Service    | PaaS | Highly scalable and customizable container hosting platform                                                |
| App Services          | PaaS | Web applications, a lot of enterprise web hosting features, easy to start                                  |
| Functions             | PaaS | (Function-as-a-Service/Serverless) Micro/Nano services, excellent consumption-based pricing, easy to start |

## Azure Networking Services

### Networking Services

Category of services with capability to

- Connect cloud and on-premise resources
- Protect & monitor services
- Help with application delivery

### Azure Virtual Network

- Emulation of physical networking infrastructure
- Designed for isolation, segmentation, communication, filtering, routing between resources (internet and on-premises)
- Scoped to a single region
- VNet Peering or VPN Gateway allow cross VNet communication
- Segmented into one or more subnets
- Subnets are discrete sections used for
  - effective address allocation and
  - network filtering via Network Security Groups (NSGs) or Application Security Groups (ASG)

### Azure VPN Gateway

- On-premises to Azure traffic over the public internet (encrypted)
- Cross-regional communication of Azure Virtual Networks
  - VNet Peering vs VPN Gateway should be chosen based on organization needs

### Azure Load Balancer

- Even traffic distribution
- Supports both inbound and outbound scenarios
- High-availability and scalability scenarios
- Supports both TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) applications
- External and Internal traffic

### Azure Application Gateway

- Web Traffic load balancer
- Web application firewall
- Redirection
- Session affinity
- URL Routing
- SSL Termination

### Azure Content Delivery Network

- Deliver static web content to users
- Minimize Latency
- POP (points of presence) locations

## Azure Storage Services

### Types of Data

#### Structured Data

Structured data is data whose elements are addressable for effective analysis. It has been organized into a formatted repository that is typically a database. It concerns all data which can be stored in database SQL in a table with rows and columns.

#### Semi-Structured Data

Semi-structured data is information that does not reside in a relational database but that has some organizational properties that make it easier to analyze.

#### Unstructured Data

Data which is not organized in a predefined manner or does not have a predefined data model, thus it is not a good fit for a mainstream relational database.

### Azure Blob Storage

- Designed for storage of files of any kind (unstructured) \
  (BLOB - Binary Large OBject - file)
- Three storage tiers
  - Hot - frequently accessed data
  - Cool - infrequently accessed data (lower availability, high durability)
  - Archive - rarely (if-ever) accessed data

### Azure Queue Storage

- Storage of small pieces of data
- Designed for scalable asynchronous processing

### Azure Table Storage

- Storage for semi-structured data (NoSQL)
  - No need for foreign joins, foreign keys, relationships or strict schema
  - Designed for fast access
- Many programming interfaces and SDKs

### Azure File Storage

- Storage for files accessed via shared drive protocols
- Designed to extend on-premise file shares or implement **lift-and-shift** scenarios
- Similar to Blob storage, but uses SMB protocol to share files
- Provides persistent storage capability for VM

### Azure Storage Account

- Group of services which include
  - blob storage
  - table storage
  - queue storage
  - file storage
- Used to store
  - files,
  - messages, and
  - semi-structured data
- Highly scalable (up to petabytes of data)
- Highly durable (99.99999999999% - 11 nines, up to 16 nines)
- Cheapest per GB storage

### Azure Disk Storage

- Disk emulation in the cloud
- Persistent storage for Virtual Machines
- Different
  - sizes,
  - types (SSD, HDD),
  - performance tiers
- Disk can be unmanaged (not managed by cloud provider) or managed (hides complexity of managing disk)
- Provides persistent storage capability for VM
