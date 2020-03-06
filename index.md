# Introduction

Secure Device Onboard is a flexible software solution that simplifies and automates the process of onboarding IoT devices. By “onboard” we mean the process by which a device establishes its first trusted connection with a device management service.  

Today, organizations that deploy IoT devices are struggling with manual methods to securely connect devices with IoT platforms. Traditional onboarding processes are time intensive and require IT expertise. The Secure Device Onboard solution simplifies this process for end customers while simultaneously establishing trust across all organizations who manufacture, distribute, or sell the device and associated IoT solutions.   

During deployment of a device enable with the Secure Device Onboard solution, all the installer needs to do is add power to the device and connect it to the Internet. The device automatically and rapidly connects to the IoT platform in a secure and trusted manner. Secure Device Onboard combines embedded hardware security credentials with a chain-of-ownership security credential and Rendezvous service to secure the onboarding process and broker the connection to the authorized device management service provider. Today Secure Device Onboard supports Intel® Enhanced Privacy ID (Intel® EPID) and Elliptic Curve Digital Signature Algorithm-based embedded hardware security credentials.

Devices enabled with Secure Device Onboard technology work with any IoT cloud service providers that have enabled their service to work with Secure Device Onboard. This allows manufacturers to reduce the number of SKUs they need to securely connect with cloud services. 

# Secure Device Onboard Entities

The Secure Device Onboard process involves interactions between a number of different entities that participate in the process.  Those include:

**Manufacturer** - The manufacture is responsible for loading Secure Device Credentials into a device. They are also directly or indirectly responsible for installing software onto the device that supports the Secure Device Onboard protocols required for device discovery and transfer of ownership.

**Device** - The device runs software which supports the Secure Device Onboard protocols required for devices.  The device is initialized with credentials which securely identifies the device.

**Owner** - When a device is transferred to an owner who intends to install the device in their network, the owner (typically the owner's IOT Platform Service) contacts a Rendezvous Service to register the device and indicate where the device is to make contact with the IOT Platform Service.

**Rendezvous Service** - One or more Rendezvous Services operates on the Internet (or in some cases on an intranet). The Rendezvous service supports device registration by the owner (described above) and also provides a well-known endpoint that devices can connect to discover how to contact their owner's IOT Platform Service. The Rendezvous Service supports the Secure Device Onboard protocols required for owner registration and device discovery.

**IOT Platform Service** - Owners of devices typically use a IOT Platform service (also known as a Device Management Service) to manage their devices. The IOT Platform Service must support the Secure Device Onboard protocols required to register devices with the Rendezvous service and to provide devices with the information required to connect to the owner’s network. 


# Secure Device Onboard Protocol Specification

The Secure Device Onboard Protocol Specification defines a set of protocols for communications between the entities that participate in the Secure Device Onboard process.  Those protocols are: 

**Device Initialization Protocol (DI)** -  This protocol defines how credentials are inserted into a device during the manufacturing process.

**Transfer Ownership Protocol 0 (TO0)** -  This protocol defines how an owner of a device enabled with Secure Device Onboard communicates with a Rendezvous Service to indicate tha it has taken ownership of a device. 

**Transfer Ownership Protocol 1 (TO1)** -  This protocol defines how a device communicates with a Rendezvous Service to identify itself and discover how to make contact with its owners IOT Platform.

**Transfer Ownership Protocol 2 (TO2)** -  This protocol defines how a device communicates with its owners IOT Platform to establish trust and transfer ownership.

Details of the Secure Device Onboard protocol can be found in the *Secure Device Onboard Protocol Specification*.

# Secure Device Onboard Software

The Secure Device Onboard project provides software that helps simplify the implementation of an end-to-end Secure Device Onboard capability.  The following components are available:

**Client SDK** - THe Client SDK provides devices with an implementation of the DI protocol, which initializes the device with credentials, the TO1 protocol, which connects the device to a Rendezvous Service, and the TO2 Protocol, which connects the device to an IOT Platform Service.  The Client SDK supports Linux on X86 processors, as well as Linus and SELinux on ARM processors.

**Manufacturing Toolkit** - The Manufacturing Toolkit software enables the manufacturer to load credential into devices.  It implements the DI protocol, and includes support for database storage of credentials and is designed to integrate into the manufacturers IT processes.

**Reseller Toolkit** - The Reseller Toolkit enables distributors and System Integrators to manage the ownership credential over the devices lifetime.  It implements the DI protocol.

**Rendezvous Service** - The Rendezvous Service software provides a complete Rendezvous service, and implements the TO0 and TO1 protocols required for device registration and discovery.  It can be run in the cloud or on-premise and includes an interface to support key attestation.

**IOT Platform SDK** - The IOT Platform SDK provides micro-services to facilitate integration of an IOT Platform in the Secure Device Onboard processes. It implements the TOO protocol required for device registration, and the TO2 protocol required for device ownership transfer.

**Customer Reference Implementation** - The *Customer Reference Implementation* provides a self-contained implementation of the Secure Device Onboard protocols, which can be used as a reference implementation, as a place to get started prototyping new protocol features, or as a validation tool


# The Secure Device Onboard Process

This section describes a typical process in which Secure Device Onboard is used to automatically and securely onboard a device onto an owners network.  Those process include:

**Device Initialization** - A manufacturer initializes a device enabled with Secure Device Onboard Client software by setting the initial credentials in the device’s firmware, copying required files to the device’s OS, and storing the required security data in a backend IT system. 

**Credential Management** – The manufacturers and supply chain integrators run a tool to manage security keys and ownership credentials that correspond to each device. These credentials do not reside on the device and are used to negotiate trust as devices are bought and sold.  

**Transfer To IoT Platform** – The ownership credentials are imported into an Intel SDO-enabled IoT Platform. 

**Device Registration** – The ownership credentials are synchronized between the device management service and the rendezvous server.   

**Onboarding** - The process of verifying the device identity with the rendezvous server and brokering a trusted connection to the intended IoT platform when a device is powered on and connected to the Internet. 

The following diagram shows an example of a possible IoT supply chain and the steps taken by each participant in the Secure Device Onboard service. Each step is described in more detail in follwing sections. 

