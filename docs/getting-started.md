# First contact with NUBOMEDIA

At the heart of NUBOMEDIA we find the **Kurento Media Server** (KMS). KMS provides media capabilities to the NUBOMEDIA platform that can be used for creating a cloud media plane with the appropriate media capabilities and suitable for working with elastic scalability. This means that the number of KMS's is controlled by the NUBOMEDIA PaaS, scaling in and out depending on the load of the system.

Therefore, the first step to become a NUBOMEDIA developer, it is important to get in touch with Kurento. To that aim, it is recommended to take a look to the [Kurento documentation](http://doc-kurento.readthedocs.io/). A simple way to learn about Kurento is to follow these steps:

1. Read and understand the [Kurento basis](http://doc-kurento.readthedocs.io/en/stable/introducing_kurento.html)
2. [Install KMS](http://doc-kurento.readthedocs.io/en/stable/installation_guide.html) in your local machine (Ubuntu)
3. Run the [kurento-hello-wold](http://doc-kurento.readthedocs.io/en/stable/tutorials/java/tutorial-helloworld.html) Java tutorial in your local environment

Once you completed this process, the next step is to use NUBOMEDIA to deploy and leverage our application in a cloud environment. In short, you can see NUBOMEDIA as a development platform with different scaffolding technologies:

- The **NUBOMEDIA APIs and SDKs**. NUBOMEDIA has been made for developers, and so, on the one hand a complete set of Java APIs is provided. On the other hand, SDKs for mobile development (for Android and iOS) is also provided out of the box by NUBOMEDIA. Above in this page you can find an overview of the different APIs and SDKs, which are explained in detail in next sections of this documentation. 
- The **NUBOMEDIA PaaS Manager**. The PaaS manager can be seen as a tool aimed to control the way in which the NUBOMEDIA applications are built and deployed inside the NUBOMEDIA PaaS. Please keep reading to find more details. 

# NUBOMEDIA APIs and SDKs

From the developer’s perspective, NUBOMEDIA capabilities are accessed through a set of APIs. Hence, for creating NUBOMEDIA applications, developers just need to understand these NUBOMEDIA Development APIs so that they may use them for creating their rich RTC media applications. NUBOMEDIA offers a complete set of APIs that can be classified in three groups:

- **Media Capabilities APIs**. These APIs expose to the application logic the low-level media capabilities of NUBOMEDIA: [Media](./api/media.md), [WebRtcPeer](./api/webrtcpeer.md), and [Repository](./api/repository.md) API.
- **Signaling APIs**. The media capabilities APIs (Media, WebRtcPeer, Repository API) are signaling agnostic, meaning that they neither require nor assume any kind of specific characteristic for signaling. Hence, NUBOMEDIA capabilities can be accessed through any kind of signaling protocol including SIP, XMPP or REST. However, for simplifying common development tasks, NUBOMEDIA provides a simple [Signaling](./api/signaling.md) API based on JSON-RPCs that is suitable for most applications not requiring specific interoperability features.
- **Abstract Communication APIs**. Developers typically use RTC media capabilities for creating applications devoted to person-to-person communications. In this case, the application business logic needs to manage the communication topologies among participants in an RTC multimedia session. In the general case, this logic needs to be programmed by the application developers. However, there are a number of communication topologies that are quite  popular and appear systematically in applications. Due to this, in our architecture, we propose specific communication API abstracting the low level details of the media logic on these topologies so that developers may use them in an agile and efficient manner. In particular, we have identified two of these common topologies: the [Room](./api/room.md) and the [Tree](./api/tree.md) topology.

All in all, NUBOMEDIA offers six different APIs. The following table provides a brief summary of these APIs:

API                                   | Description
--------------------------------------| -----------
[Media API](./api/media.md)           | Enables developers consuming the **Media Server** capabilities among which we can find media transport, media archiving, media processing, media transcoding, etc.
[WebRtcPeer API](./api/webrtcpeer.md) | Abstracts the **client WebRTC** media capabilities, exposing the media capture and communication capabilities of a browser in a simple, seamless and unified way
[Repository API](./api/repository.md) | Makes possible to access an elastic scalable **media repository** for archiving media information and meta-information
[Signaling API](./api/signaling.md)   | Provides a simple signaling mechanism based on **JSON-RPCs** for applications. This API has can be used both in the application-server and in the client side
[Room API](./api/room.md)             | Enables application developers functionalities to create **group communication** applications adapted to real social interactions. This API has can be used both in the application-server and in the client side
[Tree API](./api/tree.md)             | Allows developers to build video **broadcasting** web applications. This API has can be used both in the application-server and in the client side

In addition, NUBOMEDIA offers a complete SDK to create mobile applications consuming the media capabilities provided by the NUBOMEDIA applications. You can find the following SDKs:

SDK                             | Description
--------------------------------| -----------
[Android SDK](./sdk/android.md) | **Android** version of the client-side NUBOMEDIA APIs: WebRtcPeer, Signalling, Room, Tree
[iOS SDK](./sdk/ios.md)         | Complete SDK to provide NUBOMEDIA client capabilities to **iOS** devices

This set of APIs/SDKs is inspired by the popular Web three tier model. In this model, we can distinguish three layers:

- The *Client*, typically which consists on a web browser executing the client-side application logic. This logic is typically developed using programming languages such HTML and JavaScript, and with the help of specialized third party APIs (e.g. Angular, Bootstrap, etc.)
- The *Application Server (AS)*, which hosts the server-side application logic. This layer typically contains the business logic of the application.
- The *Service Layer* comprise a number of services that are required for the application to work. In NUBOMEDIA, this layer is composed by a set of **Media Servers** (namely, [Kurento Media Server](http://doc-kurento.readthedocs.io/en/stable/introducing_kurento.html)) and a **Media Repository**  (i.e. the [Kurento Repository](http://doc-kurento-repository.readthedocs.org/)).

In the following diagram we can see how the different NUBOMEDIA APIs/SDKs fits in this three-tier model:

![NUBOMEDIA Tree Tier Model](./img/nubomedia-schema.png)

*NUBOMEDIA Tree Tier Model (clients -- application-server -- service-layer)*

# NUBOMEDIA PaaS Manager

NUBOMEDIA is a PaaS, as therefore it makes possible to upload, deploy and execute developers’ applications written in the **Java programming language** with the NUBOMEDIA APIs described before. NUBOMEDIA PaaS elastically provides the **service layer infrastructure** (i.e. the needed instances of KMSs and a Media repository if needed) depending on the load of the system.

The capabilities provided by the Paas Manager can be used by developers in two ways:

1. Using the PaaS GUI. The PaaS Manager GUI is a web application that allow to use the NUBOMEDIA PaaS Manager. This application can be found in the following [link](http://paas-manager.nubomedia.eu:8081/) (the snapshots below show some examples of this GUI). Currently the access to this application is restricted. Nevertheless, if you need access to this application, please request for the credentials using in the [NUBOMEDIA development mailing list](https://groups.google.com/forum/#!forum/nubomedia-dev).
2. Using the PaaS Manager API. In addition to the GUI, the PaaS Manager exposes its capabilities by means of a REST API. Please take a look to the [PaaS API](./paas/paas-api.md) documentation for further details.

![NUBOMEDIA PaaS Manager GUI Snapshots](./img/paas-manager.png)

*NUBOMEDIA PaaS Manager GUI Snapshots*

The **application server** is also provided by the NUBOMEDIA PaaS. Due to the fact that the applications are made in Java, we recommend to use [Spring-Boot](http://projects.spring.io/spring-boot/) as the application server side technology. Spring-Boot embeds a Tomcat server in a simple seamless way for developers. Please take a look to the [tutorials](./tutorial/nubomedia-magic-mirror.md) for examples.

# What's next

Now that you are familiar with the NUBOMEDIA technology, you can create your own applications. To do that, you simply has to follow these steps:

1. Think about your application with media capabilities
2. Chose the NUBOMEDIA [APIs](./api/media.md)/[SDKs](./sdk/android.md) needed to implement it. NUBOMEDIA provides several running [tutorials](./tutorial/nubomedia-magic-mirror.md) that can be used as templates to create new applications 
3. Deploy it in the PaaS Manager with the [PaaS GUI](./paas/paas-gui.md) or [PaaS API](./paas/paas-api.md)

Moreover, NUBOMEDIA offers additional advanced features. Take a look to this documentation to know more about [Video Content Analysis](./filter/video-content-analysis.md), [Visual Development Tool](./tools/visual-development-tools.md), [monitoring tools](./tools/monitoring-tools.md), or [NUBOMEDIA Architecture](./advanced/nubomedia_architecture.md).
