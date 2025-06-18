## Pre-Implementation Considerations

The KNX control protocol is used largely throughout the United Kingdom and Europe. It is an approved standard in the following areas:

- European Standard (CENELEC EN 50090 and CEN EN 13321-1).
- International Standard (ISO/IEC 14543-3).
- Chinese Standard (GB/Z 20965).
- US Standard (ANSI/ASHRAE 135).

Prior to implementing KNX into your Control4 system, it is recommended that the following resources be reviewed: 

[http://www.knx.org][1]

This is the official site of the KNX association. It provides an excellent starting point in understanding KNX architecture and requirements.

It is important to note that this release of KNX support is targeted to early adopters who have experience with the KNX protocol and have the ability (or access to a resource) to work with an ETS (Engineering Tool software) to configure KNX Group Address and Object Functions. The scope of this document does not include instruction on designing and configuring KNX device functionality. 

This document is intended to outline the steps required to use the delivered device drivers to support KNX certified dimmers, switches and keypads within a Control4 system. It assumes that the KNX devices are already configured with the appropriate Group Address values.

Note that all examples provided in this document are based off a KNX device Configuration using ETS5.

[1]:	[http://www.knx.org]