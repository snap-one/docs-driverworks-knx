## Introduction to KNX Driver Development

Control4 supports integration with device drivers using the standardized KNX control network topology. The purpose of this section is to provide a starting point for third party and partner level KNX driver development. Its focus is on defining an API layer that is available for a KNX driver to use in order to communicate with both the KNX Network layer as it resides within the Control4 environment, as well as other KNX devices.

The content defines each of the APIs with a description, parameter list and an example. Further examples are referenced within the KNX drivers provided in SDK. It is recommended that these drivers be reviewed in conjunction with this document before beginning KNX driver development. Finally, all of the currently supported Datapoint Types (DPTs) are defined at the end of the document.

Note that this content is intended as a supplement to the existing Control4 DriverWorks SDK documentation. Its scope is KNX specific and it assumes knowledge in KNX topology and standards exists. Also, if you are new to writing drivers targeted for the Control4 environment, it is strongly recommended that a review of the DriverWorks SDK occur before continuing.
