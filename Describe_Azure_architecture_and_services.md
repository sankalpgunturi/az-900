# Describe Azure architecture and services

## Geographies, Regions & Availability Zones

### What is a Data Center?

- Key Characteristics
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
  - Some services are ~global services~, as such are not assigned/deployed in specific region (E.g. Traffic Manager for DNS routing, Azure Active Directory)
  - Globally available with 50+ regions
  - Special government regions (US DoD Central, US Gov Virginia, etc.)
  - Special partnered regions (China East, China North)
  - [Azure Latency Test](https://www.azurespeed.com/Azure/Latency)
  - [Azure Products availability by region](https://azure.microsoft.com/en-us/explore/global-infrastructure/products-by-region/)

#### Availability Zones

- Key Characteristics
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

- Key Characteristics
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