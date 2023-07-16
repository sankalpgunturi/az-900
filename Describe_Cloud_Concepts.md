# Describe Cloud Concepts

## Cloud Computing and Vocabulary

### What is Cloud Computing?

Cloud computing is a delivery model for services like:

- Storage (files, databases)
- Compute Power (Linux, Windows, Web)
- Networking
- Analytics (Performance data, Telemetry)
- and many more...
  over the internet

### What are the key characteristics of Cloud Computing

- **Scalability**: The ability to scale. It is a process of allocating and deallocating resources
  - Types of scaling:
    - Vertical Scaling: Scaling up and Scaling down (CPU Memory Storage)
    - Horizontal Scaling: Scaling in and Scaling out (Amount)
- **Elasticity**: The ability to scale dynamically.
- **Agility**: The ability to react quickly. It is the ability to allocate and deallocate (scale) resources quickly.
- **Fault Tolerance**: It is the ability to remain up and running during component and service failures.
- **Disaster Recovery**:
  - **Disaster** is a serious disruption of services caused by natural or human-induced causes.
  - **Disaster Recovery** is the ability to recover from an event that has taken down the service (disaster).
- **High Availability**:
  - $Availability$ = $\frac{Uptime}{Uptime + Downtime}$ = A measure of system uptime for users/services.
  - **High Availability** is the ability to keep services running for extended periods of time with very little downtime.

## Economies of Scale

- Cost per unit (service) lowers as the size of the company grows.

## CapEx vs OpEx

### CapEx

- Key Characteristics
  - Own Infrastructure
  - Big Initial Investment
  - Lots of maintenance required
    - Support staff
    - Power and Networking
    - Hardware Failures
    - Others

### OpEx

- Key Characteristics
  - Rent infrastructure
  - No intial investment, pay for what you use
  - Minimal Maintenance
    - Operations Team

### Comparison

| **Attributes**    | **CapEx**   | **OpEx**       |
| ----------------- | ----------- | -------------- |
| Upfront Cost      | Significant | None           |
| Ongoing Cost      | Low         | Based on Usage |
| Tax Deduction     | Over time   | Same year      |
| Early Termination | No          | Anytime        |
| Maintenance       | Significant | Low            |
| Value over time   | Lowers      | No change      |

## Consumption-Based Model

- Key Characteristics
  - No upfront cost
  - No wasted resources
  - Pay for additional resources when needed
  - Stop paying at any time
  - Multiple pricing components per service
  - Very granular usage measurement

## IaaS vs Paas vs SaaS

### IaaS

- Key Characteristics
  - Ownership
    - Cloud provider manages infrastructure
      - Infrastructure - networking, hardware & virtualization
    - You manage platform & software
      - Platform - operating system, middleware, runtime
      - Software - data & applications
  - Use Cases
    - Migration of workloads
    - Test & Development
    - Storage, backups and recovery
    - E.g. Virtual Machine, Virtual Network, Managed Disk

### PaaS

- Key Characteristics
  - Ownership
    - Cloud provider manages infrastructure & platform
      - Infrastructure - networking, hardware & virtualization
      - Platform - operating system, middleware, runtime
    - You manage software
      - Software - data & applications
  - Use Cases
    - Development framework
    - Analytics & business intelligence
    - Examples:
      - SQL (for relational databases)
      - App Service (for web-hosting)
      - Logic Apps (for enterprise integrations)
      - Function Apps (for serverless applications)

### SaaS

- Key Characteristics
  - Ownership
    - Cloud provider manages infrastructure, platform & software
      - Infrastructure - networking, hardware & virtualization
      - Platform - operating system, middleware, runtime
      - Software - data & applications
    - You manage nothing
  - Use Cases
    - Buying of-the-shell applications
    - E.g. OneDrive, Outlook, Skype

## Public, Private & Hybrid Cloud Deployment Models

### Public Cloud

- Key Characteristics
  - Everything runs on cloud provider hardware
  - No local hardware
  - Some services share hardware with other customers
- Advantages and Disadvantages
  |**Advantages**|**Disadvantages**|
  |---|---|
  |No CapEx| Security & Complaince|
  |High Availability & Agility| Lack of Ownership|
  |Pay-as-you-go pricing|Specific scenarios with unique business requirements|
  |No hardware maintenance| |
  |No deep technical skills required| |

### Private Cloud

- Key Characteristics
  - Everything runs on your own datacenter
  - Self-service should be provided
  - You maintain all the hardware
- Advantages & Disadvantages
  **Advantages**|**Disadvantages**
  ---|---
  Can support any scenario | Intial CapEx
  Control over security | Limited Agility
  Can meet any security & complaince requirements | IT skills & expertise are mandatory

### Hybrid Cloud

- Key Characteristics
  - Combines public & private clouds
  - Great flexibility
- Advantages & Disadvantages
  **Advantages**|**Disadvantages**
  ---|---
  Great flexibility | Can be more expensive
  Run legacy apps in private cloud | Complicated to manage
  Utilize existing infrastructure | IT skills & expertise are mandatory
  Meet any security requirements |
