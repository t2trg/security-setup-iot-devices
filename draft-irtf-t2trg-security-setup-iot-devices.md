---
stand_alone: true
ipr: trust200902
docname: draft-irtf-t2trg-security-setup-iot-devices-latest
cat: info
pi:
  toc: 'yes'
  compact: 'yes'
  symrefs: 'yes'
  sortrefs: 'yes'
  iprnotified: 'no'
  strict: 'yes'
title: 'Terminology and processes for initial security setup of IoT devices'
abbrev: IoT initial security setup
author:
- ins: M. Sethi
  name: Mohit Sethi
  org: Aalto University
  street:
  city: Espoo
  region: ''
  code: '02150'
  country: Finland
  email: mohit@iki.fi
- ins: B. Sarikaya
  name: Behcet Sarikaya
  org:
  street:
  - ''
  - ''
  city: ''
  region: ''
  code: ''
  country: ''
  email: sarikaya@ieee.org
- ins: D. Garcia-Carrillo
  name: Dan Garcia-Carrillo
  org: University of Oviedo
  street: ''
  city: Oviedo
  region: ''
  code: '33207'
  country: Spain
  email: garciadan@uniovi.es
informative:
  RFC2904:
  RFC4291:
  RFC5272:
  RFC6241:
  RFC7030:
  RFC7228:
  RFC7252:
  RFC7230:
  RFC8040:
  RFC8366:
  RFC8376:
  RFC8572:
  RFC8949:
  RFC8995:
  RFC9140:
  RFC9148:
  simpleconn:
    target: https://www.wi-fi.org/download.php?file=/sites/default/files/private/Wi-Fi_Simple_Configuration_Technical_Specification_v2.0.7.pdf
    title: Wi-Fi Simple Configuration
    author:
    - org: Wi-Fi Alliance
    date: 2019
    seriesinfo:
      Version: 2.0.7
  Sethi14:
    target: http://dx.doi.org/10.1145/2632048.2632049
    title: Secure Bootstrapping of Cloud-Managed Ubiquitous Displays
    author:
    - ins: M. Sethi
      name: Mohit Sethi
      org: Ericsson
    - ins: E. Oat
      name: Elena Oat
      org: Aalto University
    - ins: M. Di Francesco
      name: Mario Di Francesco
      org: Aalto University
    - ins: T. Aura
      name: Tuomas Aura
      org: Aalto University
    date: 2014-09
    seriesinfo:
      Proceedings: of ACM International Joint Conference on Pervasive and Ubiquitous Computing (UbiComp 2014), pp. 739-750, Seattle, USA
  dpp:
    target: https://www.wi-fi.org/wi-fi-download/35330
    title: Wi-Fi Easy Connect Specification
    author:
    - org: Wi-Fi Alliance
    date: 2018
    seriesinfo:
      Wi-Fi Alliance: 'Version 3.0'
  LoRaWAN:
    target: https://lora-alliance.org/resource_hub/lorawan-specification-v1-1/
    title: LoRa Specification
    author:
    - org: LoRa Alliance
    date: 2017-10
    seriesinfo:
      LoRa Alliance: 'Version: 1.1'
  oma:
    target: https://openmobilealliance.org/release/LightweightM2M/V1_2_1-20221209-A/OMA-TS-LightweightM2M_Core-V1_2_1-20221209-A.pdf
    title: 'Lightweight Machine to Machine Technical Specification: Core'
    author:
    - org: Open Mobile Alliance
    date: 2022-12
    seriesinfo:
      'Approved Version': 1.2.1
  oma-transport:
    target: https://www.openmobilealliance.org/release/LightweightM2M/V1_2_1-20221209-A/OMA-TS-LightweightM2M_Transport-V1_2_1-20221209-A.pdf
    title: 'Lightweight Machine to Machine Technical Specification: Transport Bindings'
    author:
    - org: Open Mobile Alliance
    date: 2022-12
    seriesinfo:
      'Approved Version': 1.2.1
  ocf:
    target: https://openconnectivity.org/specs/OCF_Security_Specification.pdf
    title: OCF Security Specification
    author:
    - org: Open Connectivity Foundation
    date: 2022-10
    seriesinfo:
      Version: 2.2.6
  ieee8021ar:
    target: https://1.ieee802.org/security/802-1ar/
    title: IEEE Standard for Local and metropolitan area networks–Secure Device Identity
    author:
    - org: IEEE
    date: 2018
  ieee8021x:
    target: https://1.ieee802.org/security/802-1x/
    title: IEEE Standard for Local and metropolitan area networks–Port-Based Network Access Control
    author:
    - org: IEEE
    date: 2020
  threadcommissioning:
    title: Thread Commissioning
    author:
    - org: Thread Group
    date: 2015
  fidospec:
    target: https://fidoalliance.org/specifications/download-iot-specifications/
    title: FIDO Device Onboard Specification
    author:
    - org: Fast Identity Online Alliance
    date: 2022-04
    seriesinfo:
      Fido Alliance: 'Version: 1.1'
--- abstract


This document provides an overview of terms that are commonly used when discussing the initial security setup of Internet of Things (IoT) devices. This document also presents a brief but illustrative survey of protocols and standards available for initial security setup of IoT devices. For each protocol, we identify the terminology used, the entities involved, the initial assumptions, the processes necessary for completion, and the knowledge imparted to the IoT devices after the setup is complete.

--- middle

# Introduction

Initial security setup for a device refers to any process that takes place before a device can become fully operational. The phrase **initial security setup** intentionally includes the term *security* as setup of devices without adequate security or with insecure processes is no longer acceptable. The initial security setup process, among other things, involves network discovery and selection, access authentication, configuration of necessary credentials and parameters.

Initial security setup for IoT devices is challenging because the size of an IoT network varies from a couple of devices to tens of thousands, depending on the application. Moreover, devices in IoT networks are produced by a variety of vendors and are typically heterogeneous in terms of the constraints on their power supply, communication capability, computation capacity, and user interfaces available. This challenge of initial security setup in IoT was identified by [Sethi et al.](#Sethi14) while developing a solution for smart displays.

Initial security setup of devices typically also involves providing them with some sort of network connectivity. The functionality of a disconnected device is rather limited. Initial security setup of devices often assumes that some network has been setup a-priori. Setting up and maintaining a network itself is challenging. For example, users may need to configure the network name (called as Service Set Identifier (SSID) in Wi-Fi networks) and passphrase before new devices can be setup. Specifications such as the Wi-Fi Alliance Simple Configuration {{simpleconn}} help users setup networks. However, this document is only focused on terminology and processes associated with initial security setup of devices and excludes any discussion on setting up networks.

There are several terms that are used in the context of initial security setup of devices:

* Bootstrapping

* Provisioning

* Onboarding

* Enrollment

* Commissioning

* Initialization

* Configuration

* Registration

* Discovery

In addition to using a variety of different terms, initial security setup mechanisms can rely on a number of entities. For example, a companion smartphone device maybe necessary for some initial security setup mechanisms. Moreover, security setup procedures have diverse initial assumptions about the device being setup. As an example, an initial security setup mechanism may assume that the device is provisioned with a pre-shared key and a list of trusted network identifiers. Finally, initial security setup mechanisms impart different information to the device after completion. For example, some mechanisms may only provide a key for use with an authorization server, while others may configure elaborate access control lists directly.

The next section provides an overview of some standards and protocols for initial security setup of IoT devices. For each mechanism, the following are explicitly identified:

* Terminology used

* Entities or "players" involved

* Initial assumptions about the device

* Processes necessary for completion

* Knowledge imparted to the device after completion




# Standards and Protocols {#usage}


## Bluetooth

Bluetooth mesh specifies a provisioning protocol.  The goal of the provisioning phase is to securely incorporate a new Bluetooth mesh node, by completing two critical tasks. First, to authenticate the unprovisioned device and second, to create a secure link with said device to share information.

The provisioning process is divided into five distinct stages summarize next:

   * Beaconing for discover: The new unprovisioned device is discovered by the provisioner

   * Negotiation: The unprovisioned device indicates to the provisioner a set of capabilities such as the security algorithms supported, the availability of its public key using an Out-of-Band (OOB) channel and the input/output interfaces supported

   * Public-key exchange: The authentication method is selected by the provisioner and both devices exchange Elliptic-curve Diffie–Hellman (ECDH) public keys. These keys may be static or ephemeral. Their exchange can be done in two ways, either via Out-of-Band or directly through a Bluetooth link. Each device then generates a symmetric key, named ECDHSecret, by combining its own private key and the public key of the peer device. The EDCHSecret is used to protect communication between the two devices.


  * Authentication: During this phase, the ECDH key exchange is authenticated. The authentication method can be Output OOB, Input OOB, static OOB, or No OOB. With Output OOB, the unprovisioned device chooses a random number and outputs that number in manner consistent with its capabilities. The provisioner then inputs this number. Then, a check confirmation value operation is performed. This involves a cryptographic exchange regarding (in this case) the random number to complete the authentication. With Input OOB, the roles are reversed, being the provisioner the entity that generates the random number. When neither of the previous authentication procedures are feasible, both the provisioner and unprovisioned device generate a random number and require the user supervising the setup to verify that values on the device and provisioner are the same.


  * Distribution of provisioning data: At this point, the provisioning process can be protected. This involves the distribution of data such as a Network key, to secure the communications at network layer and a unicast address among other information.


Bluetooth mesh has the following characteristics:

  * Terms: Configuration, discovery, provisioning.
  * Players: Client, Device, Manager, Manufacturer, Peer, Server, User
  * Initial beliefs assumed in the device: Previously to the provisioning phase, there is no pre-shared credentials for a trust relation.
  * Processes: Provisioning
  * Beliefs imparted to the device after protocol execution: After the provisiong, the device trusts the provisioner entity and any other device in the network sharing its network key.

## Device Provisioning Protocol (DPP)

The Wi-Fi Alliance Device provisioning protocol (DPP) {{dpp}} describes itself as a standardized protocol for providing user friendly Wi-Fi setup while maintaining or increasing the security. DPP relies on a configurator, e.g. a smartphone application, for setting up all other devices, called enrollees, in the network. DPP has the following three phases/sub-protocols:

* Bootstrapping: The configurator obtains bootstrapping information from the enrollee using an out-of-band channel such as scanning a QR code or tapping NFC. The bootstrapping information includes the public-key of the device and metadata such as the radio channel on which the device is listening.

* Authentication: In DPP, either the configurator or the enrollee can initiate the authentication protocol. The side initiating the authentication protocol is called as the initiator while the other side is called the responder. The authentication sub-protocol provides authentication of the responder to an initiator. It can optionally authenticate the initiator to the responder (only if the bootstrapping information was exchange out-of-band in both directions).

* Configuration: Using the key established from the authentication protocol, the enrollee asks the configurator for network information such as the SSID and passphrase of the access point.

DPP has the following characteristics:

  * Terms: Bootstrapping, configuration, discovery, enrollment, provisioning.
  * Players: Authenticator, Client, Configurator, Device, Initiator, Manufacturer, Owner, Peer, Persona, Responder, User, Enrollee
  * Initial beliefs assumed in the device: There are two entities involved in the DPP protocol, the Initiator and Responder. These entities as a starting point do not have a trust relation, nor do they share credentials or key material. DPP uses a decentralized architecture with no central authority to coordinate or control authentication and rely on a direct trust model.
 In DPP, authentication does not rely on a pre-existing trust relation with a third-party or centralized entity, hence all entities involved in DPP need to perform the required validation.

  * Processes: Bootstrapping, authentication,  provisioning, and network access.
    Bootstrapping: To establish a secure provisioning connection, the devices exchange public bootstrapping keys.
    Authentication: To establish trust and build a secure channel, the devices employ the DPP Authentication protocol's bootstrapping keys.
    Configuration: The Configurator uses the DPP Configuration protocol to provision the Enrollee through the secure channel created during DPP Authentication.
    Network access: The Enrollee establishes network access using the newly provisioned credentials.

  * Beliefs imparted to the device after protocol execution: DPP bootstrapping relies on the transfer of the public-key that is expected to be trusted. The beliefs when mutual authentication is run, relies on the trust of a succesful DPP bootstrapping. When mutual authentication is not supported, a device that can control when and how its own public key is bootstrapped, can perform a weak authentication to any entity that knows its public key.

## Enrollment over Secure Transport (EST)

Enrollment over Secure Transport (EST) {{RFC7030}} defines a profile of Certificate Management over CMS (CMC) {{RFC5272}}. EST relies on Hypertext Transfer Protocol (HTTP) and Transport Layer Security (TLS) for exchanging CMC messages and allows client devices to obtain client certificates and associated Certification Authority (CA) certificates. A companion specification for using EST over secure CoAP has also been standardized {{RFC9148}}. EST assumes that some initial information is already distributed so that EST client and servers can perform mutual authentication before continuing with protocol. {{RFC7030}} further defines "Bootstrap Distribution of CA Certificates" which allows minimally configured EST clients to obtain initial trust anchors. It relies on human users to verify information such as the CA certificate "fingerprint" received over the unauthenticated TLS connection setup. After successful completion of this bootstrapping step, clients can proceed to the enrollment step during which they obtain client certificates and associated CA certificates.

EST has the following characteristics:

  * Terms: Bootstrapping, enrollment, initialization, configuration.
  * Players: Administrator, Client, Device, Manufacturer, Owner, Peer, Server, User
  * Initial beliefs assumed in the device: There is a process of distribution of initial information which provides both the EST client and server with the information for the EST client and server to perform mutual authentication as well as for authorization.
  * Processes: Distribution of Certificates, Bootstrap, Enrollment
  * Beliefs imparted to the device after protocol execution: The EST enrollment process is designed to make establishing automated certificate issuing from a trustworthy CA as simple as possible. After the processe have finished, the device is able to automatically renew its certificates through re-enrollment as it has a trust relation with the ESP server.




## Open Mobile Alliance (OMA) Lightweight Machine to Machine specification (LwM2M)


LwM2M specification developed by OMA {{oma}} defines a RESTful architecture where a new IoT device (LwM2M client) first contacts an LwM2M Bootstrap-Server for obtaining essential information such credentials for subsequently registering with one or more LwM2M Servers. These one or more LwM2M servers are used for performing device management actions during the device lifecycle (reading sensor data, controlling an actuator, modifying access controls etc.). LwM2M specification does not deal with the initial network configuration of IoT devices and assumes that the IoT client device has network reachability to the LwM2M Bootstrap-Server and LwM2M Server.

The current standard defines the following four bootstrapping modes:

* Factory Bootstrap: An IoT device is configured with all the information necessary for securely communicating with an LwM2M Bootstrap-Server and/or LwM2M Serverwhile it is manufactured and prior to its deployment.

* Bootstrap from Smartcard: An IoT device retrieves all the information necessary for securely communicating with an LwM2M Bootstrap-Server and/or LwM2M Server from a Smartcard.

* Client Initiated Bootstrap: If the IoT device in one of the above bootstrapping modes is only configured with information about an LwM2M Bootstrap-Server, then the client device must first communicate securely with the configured LwM2M Bootstrap-Server and obtain necessary information and credentials to subsequently register with one or more LwM2M Servers.

* Server Initiated Bootstrap: In this bootstrapping mode, the LwM2M server triggers the client device to begin the client initiated bootstrap sequence described above.

The LwM2M specification is also quite flexible in terms of the credentials and the transport security mechanism used between the client device and the LwM2M Server or the LwM2M Bootstrap-Server. Credentials such as a pre-shared symmetric key, a raw public key (RPK), or x.509 certificates can be used with various transport protocols such as Transport Layer Security (TLS) or Datagram Transport Layer Security (DTLS) as specified in LwM2M transport bindings specification {{oma-transport}}.

As explained earlier, an LwM2M Bootstrap-Server is responsible for provisioning credentials into an LwM2M Client. When x509 certificates are being provisioned, the asymmetric key pair is generated on the Bootstrap-Server and then sent to the LwM2M client device. This approach is not acceptable in all scenarios and therefore, LwM2M specification also supports a mode where the client device uses the Enrollment over Secure Transport (EST) certificate management protocol for provisioning certificates from the LwM2M Bootstrap-Server to the LwM2M Client.


OMA has the following characteristics:

  * **Terms**:
    * *Bootstrapping* and *Unbootstrapping*: Bootstrapping is used for describing the process of providing an IoT device with credentials and information of one or more LwM2M server. Interestingly, the transport bindings specification {{oma-transport}} also uses the term unbootstrapping for the process where objects corresponding to an LwM2M Server are deleted on the client.
    * *Provisioning* and *configuration*: terms used to refer to the process of providing some infomration to a LwM2M client.
    * *Discovery*: term for the process by which a LwM2M Bootstrap-Server or LwM2M Server discovers objects, object instances, resources, and attributes supported by RESTful interfaces of a LwM2M Client.
    * *Register* and *De-register*: Register is the process by which a client device sets up a secure association with an LwM2M Server and provides the server with information about objects and existing object instances of the client. De-register is the process by which the client deletes information about itself provided to the LwM2M server during the registration process.
    * *Intialization*: term for the process by which an LwM2M Bootstrap-Server or LwM2M Server deletes objects on the client before performing any write operations.
  * **Players**: Device manufacturers or Smartcard manufacturers are responsible for providing client IoT devices with initial information and credentials of LwM2M Bootstrap-Server and/or LwM2M server.
  * **Initial beliefs assumed in the device**: The client at the very least has necessary information to trust the LwM2M bootstrap server in the .
  * **Processes**: LwM2M does not require any actions from the device owner/user. Once the device is registered with the LwM2M server, various actions related to device management can be performed by device owner/user via the LwM2M server.
  * **Beliefs imparted to the device after protocol execution**: After the bootstrapping is performed, the LwM2M client can register (Security object and Server object) with the LwM2M servers.


## Nimble out-of-band authentication for EAP (EAP-NOOB)

Extensible Authentication Protocol (EAP) framework provides support for multiple authentication methods. EAP-NOOB {{RFC9140}} defines an EAP method where the authentication is based on a user-assisted out-of-band (OOB) channel between the IoT device (peer in EAP terminology) and the server. It is intended as a generic bootstrapping solution for IoT devices which have no pre-configured authentication credentials and which are not yet registered on the authentication server.

The application server where the IoT device is registered once EAP-NOOB is completed may belong to the manufacturer or the local network where the device is being deployed. EAP-NOOB uses the flexibility of the Authentication, Authorization, and Accounting (AAA) {{RFC2904}} architecture to allow routing of EAP-NOOB sessions to a specific application server.

EAP-NOOB claims to be more generic than most ad-hoc bootstrapping solutions in that it supports many types of OOB channels and supports IoT devices with only output (e.g. display) or only input (e.g. camera).


EAP-NOOB has the following characteristics:

  * **Terms**:
    * *Bootstrapping*: term used to describe the entire process involved during the initial security setup of an IoT device. The specification does not use separate terms or distinguish the process of obtaining identifier and credentials for communicating with an application server where the user has an account or for network connectivity.
    * *Registration*: term used for describing the process of associating the device with a user account on an application server.
  * **Players**: The device owner/user is responsible for transferring an OOB message necessary for protocol completion. The application server where the device is registered may be provided by different service providers including the device manufacturer or device owner. The local network needs standard AAA configuration for routing EAP-NOOB sessions to the application server chosen by the device owner/user.
  * **Initial beliefs assumed in the device**: EAP-NOOB does not require devices to have any pre-installed credentials but expects all devices to use a standard identifier (noob@eap-noob.arpa) during initial network discovery.
  * **Processes**: The IoT device performs network discovery and one or more OOB outputs maybe generated. The user is expected EAP exchange is encompassed by Initial Exchange, OOB step, Completion Exchange and Waiting Exchange.
  * **Beliefs imparted to the device after protocol execution**: After EAP-NOOB botstrapping process is complete, the device and server establish a long-term secret which can renewed without further user involvement. As a side-effect, the device also obtains identifier and credentials for network and Internet connectivity (via the EAP authenticator).

## Open Connectivity Foundation (OCF)

The Open Connectivity Foundation (OCF) {{ocf}} defines the process before a device is operational as onboarding.  The first step of this onboarding process is configuring the ownership, i.e., establishing a legitimate user that owns the device. For this, the user is supposed to use an Onboarding tool (OBT) and an Owner Transfer Method (OTM).

The OBT is described as a logical entity that may be implemented on a single or multiple entities such as a home gateway, a device management tool, etc. OCF lists several optional OTMs. At the end of the execution of an OTM, the onboarding tool must have provisioned an Owner Credential onto the device. The following owner transfer methods are specified:

* Just works: Performs an un-authenticated Diffie-Hellman key exchange over Datagram Transport Layer Security (DTLS). The key exchange results in a symmetric session key which is later used for provisioning. Naturally, this mode is vulnerable to on-path attackers.

* Random PIN: The device generates a PIN code that is entered into the onboarding tool by the user. This pin code is used together with TLS-PSK ciphersuites for establishing a symmetric session key. OCF recommends PIN codes to have an entropy of 40 bits.

* Manufacturer certificate: An onboarding tool authenticates the device by verifying a manufacturer installed certificate. Similarly, the device may authenticate the onboarding tool by verifying its signature.

* Vendor specific: Vendors implement their own transfer method that accommodates any specific device constraints.

Once the onboarding tool and the new device have authenticated and established secure communication, the onboarding tool provisions/configures the device with Owner credentials. Owner credentials may consist of certificates, shared keys, or Kerberos tickets for example.

The OBT additionally configures/provisions information about the Access Management Service (AMS), the Credential Management  Service (CMS), and the credentials for interacting with them. The AMS is responsible for provisioning access control entries, while the CMS provisions security credentials necessary for device operation.

OCF has the following characteristics:

  * Terms: Configuration, discovery, enrollment, onboarding, provisioning, registration,
  * Players: Client, Device, Manager, Manufacturer, Owner, Peer, Server, User
  * Initial beliefs assumed in the device: The device needs to be associated with an owner in the onboarding process and then go through the provisioning process before being considered as trustworty.
  * Processes: Onboarding, provisioning.
  * Beliefs imparted to the device after protocol execution: In the provisioning phase the device receives the necessary credentials to interact with provisioning services and any other services or devices that are part of the normal operation of the device.




## Fast IDentity Online (FIDO) alliance

The Fast IDentity Online Alliance (FIDO) is currently specifying an automatic onboarding protocol for IoT devices {{fidospec}}. The goal of this protocol is to provide a new IoT device with information for interacting securely with an online IoT platform. This protocol allows owners to choose the IoT platform for their devices at a late stage in the device lifecycle. The draft specification refers to this feature as "late binding".

The FIDO IoT protocol itself is composed of one Device Initialization (DI) protocol and 3 Transfer of Ownership (TO) protocols TO0, TO1, TO2. Protocol messages are encoded in Concise Binary Object Representation (CBOR) {{RFC8949}} and can be transported over application layer protocols such as Constrained Application Protocol (CoAP) {{RFC7252}} or directly over TCP, Bluetooth etc. FIDO IoT however assumes that the device already has IP connectivity to a rendezvous server. Establishing this initial IP connectivity is explicitly stated as "out-of-scope" but the draft specification hints at the usage of Hypertext Transfer Protocol (HTTP) {{RFC7230}} proxies for IP networks and other forms of tunnelling for non-IP networks.

The specification only provides a non-normative example of the DI protocol which must be executed in the factory during device manufacture. This protocol embeds initial ownership and manufacturing credentials into Restricted Operation Environment (ROE) on the device. The initial information embedded also includes a unique device identifier (called as GUID in the specification). After DI is executed, the manufacturer has an ownership voucher which is passed along the supply chain to the device owner.

When a device is unboxed and powered on by the new owner, the device discovers a network-local or an Internet-based rendezvous server. Protocols (TO0, TO1, and TO2) between the device, the rendezvous server, and the new owner (as the owner onboarding service) ensure that the device and the new owner are able to authenticate each other. Thereafter, the new owner establishes cryptographic control of the device and provides it with credentials of the IoT platform which the device should used.


FIDO has the following characteristics:

  * Terms: Provisioning, onboarding, commissioning, initialisation.
  * Players: Device, Manager, Manufacturer, Owner, Rendezvous Server,  User
  * Initial beliefs assumed in the device: In the initial state the device is not yet associated with a specific owner. The DI process has to take place to embed owndership and manufacturing credentials in the device, the first in a chaim to create an ownership voucher that will be used to perform the transfer of ownership of the device.

  * Processes: Device Initialize Protocol (DI), Transfer Ownership Protocol 0 (TO0), Transfer Ownership Protocol 1 (TO1), Transfer Ownership Protocol 2 (TO2)
  * Beliefs imparted to the device after protocol execution: When the device is powered on, and all TO protocols run, the device figures out by contacting with the rendezvous server, who the owner is, authenticate with the owner. At this point the rendezvous server, and owner are able to authenticate the device.



## Bootstrapping Remote Secure Key Infrastructures (BRSKI)

The ANIMA working group is working on a bootstrapping solution for devices that relies on 802.1AR {{ieee8021ar}} vendor certificates called Bootstrapping Remote Secure Key Infrastructures (BRSKI) {{RFC8995}}. In addition to vendor installed IEEE 802.1AR certificates, a vendor based service on the Internet is required. Before being authenticated, a new device only needs link-local connectivity, and does not require a routable address. When a vendor provides an Internet based service, devices can be forced to join only specific domains. The document highlights that the described solution is aimed in general at non-constrained (i.e. class 2+ defined in {{RFC7228}}) devices operating in a non-challenged network. It claims to scale to thousands of devices located in hostile environments, such as ISP provided CPE devices which are drop-shipped to the end user.

BRSKI has the following characteristics:

  * Terms: Bootstrapping, provisioning, enrollment, onboarding.
  * Players: Administrator, Client, Cloud Registrar, Configurator, Device, Domain Registrar, Initiator, Join Proxy, JRC, Manufacturer, Owner, Peer, Pledge, Server, User
  * Initial beliefs assumed in the device: Every device has an IDevID, installed and signed by the manufacturer, which is used as a basis for establishing further trust relations. In the initial stage, when the device is deployed in a specific location it cannot securely communicate with the registrar or JRC, to be integrated into the network, so  the device and the registrar need to establish mutual trust.
  * Processes: Discover, self-Identify, joint registrar, imprint registrar, enroll.
  * Beliefs imparted to the device after protocol execution: After the process has finished and the device is imprinted, and trusts the registrar/JRC, through a voucher issued by the manufacturer and verified by the device.

## Secure Zero Touch Provisioning (SZTP)

 {{RFC8572}} defines a bootstrapping strategy for enabling devices to securely obtain all the configuration information with no installer input, beyond the actual physical placement and connection of cables. Their goal is to enable a secure NETCONF {{RFC6241}} or RESTCONF {{RFC8040}} connection to the deployment specific network management system (NMS). SZTP requires the devices to be configured with trust anchors in the form of X.509 certificates. {{RFC8572}} is similar to BRSKI based on {{RFC8366}}.

SZTP has the following characteristics:

  * Terms: Bootstrapping, provisioning, onboarding, enrollment, configuration, discovery.
  * Players: Administrator, Bootstrap Server, Client, Device, Manufacturer, Onboarding Server, Owner, Redirect Server, Bootstrap Server, User, Owner
  * Initial beliefs assumed in the device: Initially, the device needs have pre-configured a state that allows allows the bootstrap processs. Among other information, the trust anchor for ownership voucher, client & intermediaries certificates, and list of trusted bootstrap servers and their trust anchors.
  * Processes: Initial state, Boot sequence, Processing bootstrapping data, validating signed data, processing redirect information, processing onboarding information.
  * Beliefs imparted to the device after protocol execution: The bootstrapping process provides the device with all the necessary information (onboarding information) to create a trust relation between the device and the bootstrap server. This allows the device to download its boot image and the necessary initial configuration. The enrollment information will allow a device to be bootstrapped and operate establishing secure connections with other systems.




## LPWAN {#lpwan}

Low Power Wide Area Network (LPWAN) encompasses a wide variety of technologies whose link-layer characteristics are severely constrained in comparison to other typical IoT link-layer technologies such as Bluetooth or IEEE 802.15.4. While some LPWAN technologies rely on proprietary bootstrapping solutions which are not publicly accessible, others simply ignore the challenge of bootstrapping and key distribution. In this section, we discuss the bootstrapping methods used by LPWAN technologies covered in {{RFC8376}}.

* LoRaWAN {{LoRaWAN}} describes its own protocol to authenticate nodes before allowing them join a LoRaWAN network. This process is called as joining and it is based on pre-shared keys (called AppKeys in the standard). The joining procedure comprises only one exchange (join-request and join-accept) between the joining node and the network server. There are several adaptations to this joining procedure that allow network servers to delegate authentication and authorization to a backend AAA infrastructure {{RFC2904}}.

* Wi-SUN Alliance Field Area Network (FAN) uses IEEE 802.1X {{ieee8021x}} and EAP-TLS for network access authentication. It performs a 4-way handshake to establish a session keys after EAP-TLS authentication.

* NB-IoT relies on the traditional 3GPP mutual authentication scheme based on a shared-secret in the Subscriber Identity Module (SIM) of the device and the mobile operator.

* Sigfox security is based on unique device identifiers and cryptographic keys. As stated in {{RFC8376}}, although the algorithms and keying details are not publicly available, there is sufficient information to indicate that bootstrapping in Sigfox is based on pre-established credentials between the device and the Sigfox network.

From the above, it is clear that all LPWAN technologies rely on pre-provisioned credentials for authentication between a new device and the network.

LPWAN has the following characteristics:

  * Terms: Provisioning, configuration, discovery.
  * Players: Administrator, Authenticator, Border Router, Client, Device, Manager, Network Server, User
  * Initial beliefs assumed in the device: The device normally has credentials that are used to directly secure the communications or to device key material to do so. There is a basic trust in the network server.
  * Processes: Provisioning
  * Beliefs imparted to the device after protocol execution: Either because of an authentication process that results in newly derived key material or the pre-provisioned key material is used, the device is able to exchange information securely through the network server.




##  Thread {#thread}

Thread Group commissioning {{threadcommissioning}} introduces a two phased process i.e. Petitioning and Joining. Entities involved are leader, joiner, commissioner, joiner router, and border router. Leader is the first device in Thread network that must be commissioned using out-of-band process and is used to inject correct user generated Commissioning Credentials (can be changed later) into Thread Network. Joiner is the node that intends to get authenticated and authorized on Thread Network. Commissioner is either within the Thread Network (Native) or connected with Thread Network via a WLAN (External).

Under some topologies, Joiner Router and Border Router facilitate the Joiner node to reach Native and External Commissioner, respectively. Petitioning begins before Joining process and is used to grant sole commissioning authority to a Commissioner. After an authorized Commissioner is designated, eligible thread devices can join network. Pair-wise key is shared between Commissioner and Joiner, network parameters (such as network name, security policy, etc.,) are sent out securely (using pair-wise key) by Joiner Router to Joiner for letting Joiner to join the Thread Network. Entities involved in Joining process depends on system topology i.e. location of Commissioner and Joiner. Thread networks only operate using IPv6. Thread devices can devise GUAs (Global Unicast Addresses) {{RFC4291}}. Provision also exist via Border Router, for Thread device to acquire individual global address by means of DHCPv6 or using SLAAC (Stateless Address Autoconfiguration) address derived with advertised network prefix.

Thread has the following characteristics:

  * Terms: Commissioning, discovery, provisioning.
  * Players: Administrator, Border Agent, Border Router, Commissioner, Commissioner Candidate, Configurator, Device, End Device, End Device, Endpoint Identifier, Initiator, Joiner, Joiner Router, Owner, Peer, Responder, Server, User
  * Initial beliefs assumed in the device: The joiner needs to share credentials with an entity that belongs to the Thread network, prior to the authentication process.
  * Processes: Petitioning, Joining
  * Beliefs imparted to the device after protocol execution: Once the authentication takes place, a trust relation is established between the Joiner and the Commissioner it receives the network parameters needed to be attached to the Thread network.

# Comparison {#comp}

There are several stages before a device becomes fully operational. There is typically a stage where some sort of credential is installed. The nature or purpose of this credential can be varied, form being part of the IoT device authentication, to a credential from a 3rd trusted party, be it the manufacturer or the owner. Solution differ on this initial process, and in some cases this can even be done in an out-of-band fashion.

After some initial credential is installed, there is a process that typically involves authentication establishing initial trust, after which  credentials and/or parameters are configured or installed into the device.

Finally, when the entities involved in the process are authenticated and the configuration and key material established, the normal operation of the IoT device can take place.


## Comparison of terminology {#comp-term}

The specifics of every term varies depending on the technology, but we enumerate here the basic terminology and what it means for the different solutions.


- Bootstrapping:
  * DPP: Client obtains the Controller’s public bootstrapping key and IP address
  * OMA: An IoT device retrieves and processes all the bootstrap data
  * EST: installation of the Explicit TA database
  * BRSKI: A protocol to obtain a local trust anchor.
  * SZTP: The process by which obtains "bootstrapping data" such as conveyed information, owner certificate and owner voucher.
  * EAP-NOOB: For an IoT device to be registered, authenticated, authorized and for it to derive key material to act as a trustworty entity in the security domain where it is deployed.

- configuration:
  * DPP: The process performed by a Configurator by which the Enrollee is provisioned.
  * OMA: Adding or removing an LwM2M Server Account to or from the LwM2M Client configuration.
  * OCF: The necessary information the Device must hold to be considered as ready for normal operation.
  * EST: The basic information (e.g., TA database) needed to initiate protocol operation.
  * SZTP: The system configuration  to be installed into the device by the bootstrapping process.
  * EAP-NOOB: Establishing  necessary information for the device to operate.
  * LPWAN: In LoRaWAN, the information related to the working of the device and protocol.

- discovery:
  * DPP: Exchange that allows obtaining specific information such as SSID, operating channel and band.
  * OCF: Making the different resources available through URIs.
  * BRSKI: Locating an entity that needs to take part of the bootstrapping process (e.g., Join proxy)

- enrollment:
  * EST: The process of obtaining the credentials needed to perform the device normal operation.
  * BRSKI: Same process describe as EST.
  * SZTP: The process of an owner joining a manufacturer's SZTP program.


- provisioning:
  * DPP: Securely enabling a device to establish secure associations with other devices in a network.
  * OMA: Establishing security credentials and access control lists by a dedicated LwM2M bootstrap server.
  * OCF: A set of processes that take place both during and after the ownership transfer. These entail configuration of credentials, and security-related resources for any services or devices that the provisioned device needs to interact with in the future.
  * Bluetooth: The procedure by which a device is authenticated, and a secure link is established, becoming a trustworthy node in the network.
  * FIDO: Same as FIDO onboarding.
  * SZTP: The set of steps that take place to enable a device to establish secure connections with other systems.
  * LPWAN: In LoRaWAN, the establishment of configuration data and credentials.


- intialization:
  * OMA: When Bootstrap-Delete operation is used, to restore a device.
  * FIDO: Protocol (DI), establishing basic information at manufacture.

- registration:
  * OMA: Establishing a registration session, which is an association between the client and the server.
  * EAP-NOOB: Add information about an IoT device in a server database.

- onboarding:
  * OCF:  The device is considered to complete the onboarding after the ownership of the Device has been transferred and the Device provisioned.
  * FIDO: The procedure of installing configuration information and secret to a device so that it may safely connect to and communicate with an IoT platform.
  * SZTP: information related to the boot image a device must be running, an initial configuration the device must commit, and scripts that the device must successfully execute.

- commissioning:
  * Thread: The process of a Thread device joining a Thread network.


- imprint:
  * BRSKI: The process by which a device obtains the needed information to act as trustworthy entity within the network or domain




## Comparison of players {#comp-players}


In this section we classify the different players.

Human User: user

Device that intends to securely join a network: pledge, device, client, peer, persona, enrollee, candidate

Entity that makes the device: Manufacturer

Entity that owns the device: owner, manager

Entity with which the device establishes a connection: IoT platform, Rendezvous Server, Server,

Entity that aids in  the process: Join Proxy, Bootstrap Server, Onboarding Server, Border Router

Person that manages a deployment or system: Administrator

Entity that steers the process for the IoT device to securely join the network: Configurator, Bootstrap Server, Rendezvous Server, JRC, Onboarding/Redirect Server, Commissioner.

External or third-party entity that intervenes in the process:  Registrar, MASA



## Comparison of initial beliefs {#comp-beliefs}

The IoT devices may have different initial beliefs depending on the credentials pre-installed, during the manufacturing process or prior to being turned on. There are cases where the initial credentials that need to be shared to establish basic trust, or they are exchanged during one of the procedures after the device is turned on, not installed during manufacturing.

### No initial trust established


EAP-NOOB does not require initial configuration of credentials to establish trust, since its done using the out-of-band process.

The OCF device starts as unowned. It has to perform an ownership transfer, to establish basic trust to perform onboarding and  provisioning. Depending on the Owener Transfer Mode (OTM) it can be considered to have not initial trust based on the credentials installed.

Bluetooth devices start as unprovisioned. Initial trust is established as a consequence of exchanging public keys and performing the authentication. If the public keys are ephemeral, there is no initial credential establishment.

### Initial trust based on the credentials installed

These credentials may very from the time of installing, and the entity to which it related. In this sense, they could be from the  manufacturer, owner or other entity.

FIDO devices have installed during the manufacturing process a set of ownership credentials (i.e., ownership voucher) and additional information to determine the current owner of the device. Hence, there is an initial trust from the IoT device and the owner. With this basic setup, and and the cooperation among device, owner and rendezvous server, the onboarding process can take place.

EST devices are configured with the needed information to perform mutual authentication and for authorization between the EST client and server.

BRSKI have manufacturer-installed certificates as starting point to establish trust.

SZTP have pre-configured initial state which provides the basis for trust.

LPWAN specifics depends on the technology, but they all have in common some pre-installed credentials that allows the establishment of trust and to secure the communications.

Thread devices, share credentials as well to establish trust.

OMA devices can have all the necessary information to start working on the network where they are deployed, if they have the factory bootstrap, hence all needed credentials to establish trust. There need to be installed some basic credentials to establish trust with the bootstrap server and perform the bootstrapping.

DPP initial trust is established during the bootstrapping where the public key is transmitted.


## Comparison of processes {#comp-process}

Analyzing the different terms used over the different solutions reviewed in this document, we can identify several processes. These are named differently in some cases, and not every technologies considers them all as part of their the following common concepts:

* To refer to the process previous to the device being turned on, in which some information, or credentials are installed into the device. This process is commonly referred to as manufacture. Is in this phase where the IoT devices have installed the needed information (specifics depend on the technology) to provide the basis for trust and to authenticate other entities.


* To refer to the process after the device is turned on and intends to locate the entity with which it has to communicate to start the authentication process to be integrated into the security domain. Here is where the device start the process to get to perform its normal operation.


* To the process by which the device obtains additional credentials, in addition to what it already had installed before being turned on.

* To the process by which the device is authenticated and established a trust relation.


## Comparison of knowledge imparted to the device {#comp-impart}


Even though the devices might start from a different place, in terms of initial credentials as basis for trust, when they finish their processes, they become trusted parties within the domain they are deployed or at least have a trust relation with a specific entity. The difference may strive in the number of trust relations are stablished during the process, as they may have not only established a trust relation with local entities where they perform their operation, but other external entities as well.

In FIDO, once the onboarding process has taken place, the IoT device is mutually authenticated with the current owner, and the needed secrets and configuration data is installed into the device, which as a result is able to connect and interact securely with the target IoT platform.

In EAP-NOOB, once the bootstrapping is completed, the IoT device not only has a trust relation with the EAP server, but the EAP authenticator can be established as well, based on the shared credentials that are derived during the authentication process.

In Bluetooth the trust is expanded to the local network as there is key material shared among the different entities of the network.

In Thread once the joiner has successfully completed the process, it can communicate directly with all Thread devices in the network.

LPWAN has a more limited scope and they usually have specific keys for applications and network communications.

EST provides the devices with the enrollment information such as certificates and symmetric keys that can be used to establish trust with different peers.

BRSKI after running it is able to verify that the communicating entities are who they claim to be, and obtain domain specific certificates to act as trustworhty entities within the domain.

SZTP after running, the device has obtained onboarding information and is equipped to establish secure connections with other systems.



# Security Considerations

This draft does not take any posture on the security properties of the different bootstrapping protocols discussed. Specific security considerations of bootstrapping protocols are present in the respective specifications.

Nonetheless, we briefly discuss some important security aspects which are not fully explored in various specifications.

Firstly, an IoT system may deal with authorization for resources and services separately from initial security setup in terms of timing as well as protocols. As an example, two resource-constrained devices A and B may perform mutual authentication using credentials provided by an offline third-party X before device A obtains authorization for running a particular application on device B from an online third-party Y. In some cases, authentication and authorization maybe tightly coupled, e.g., successful authentication also means successful authorization.

Secondly, initial security setup of IoT devices may be necessary several times during the device lifecycle since keys have limited lifetimes and devices may be lost or resold. Protocols and systems must have adequate provisions for revocation and fresh security setup. A rerun of the security setup mechanism must be as secure as the initial security setup regardless of whether it is done manually or automatically over the network.

Lastly, some IoT networks use a common group key for multicast and broadcast traffic. As the number of devices in a network increase over time, a common group key may not be scalable and the same network may need to be split into separate groups with different keys. Bootstrapping and provisioning protocols may need appropriate mechanisms for identifying and distributing keys to the current member devices of each group.



# IANA Considerations

There are no IANA considerations for this document.


# Acknowledgements

We would like to thank Tuomas Aura, Hannes Tschofenig, and Michael Richardson for providing extensive feedback as well as Rafa Marin-Lopez for his support.


--- back
