# Workshop: Reactive Messaging with Quarkus on OpenShift

In this workshop you'll learn how to implement reactive messaging functionality with Java, [Quarkus](https://quarkus.io/), [Kafka](https://kafka.apache.org/), [Vert.x](https://vertx.io/) and [MicroProfile](https://microprofile.io/). An end-to-end sample application will be deployed to [Red Hat OpenShift](https://www.openshift.com/).

The code is available as open source as part of the [Cloud Native Starter](https://github.com/IBM/cloud-native-starter/tree/master/reactive) project. 

One benefit of reactive models is the ability to update web applications by sending messages, rather than pulling for updates. This is more efficient and improves the user experience.

The workshop uses a sample application to demonstrate reactive functionality. The simple application displays links to articles and author information. 

Articles can be created via REST API. The web application receives a notification and adds the new article to the page. The animation shows how curl requests are executed at the bottom which trigger updates to the web application at the top.

<kbd><img src="images/demo-1-video-small.gif" /></kbd>

The next diagram explains the flow between the different components and microservices. 

The API client 'Submissions' triggers the REST API of the 'Articles' service to create new articles. The 'Articles' service sends a message to the 'Web-API' service via 'Kafka'. The 'Web-API' provides a streaming endpoint that the web application 'Web-App' consumes.

<kbd><img src="images/demo-1-small.png" /></kbd>

## Objectives

After you complete this workshop, you'll understand the following reactive functionality:
* Sending and receiving Kafka messages via MicroProfile
* Sending events from microservices to web applications via Server Sent Events
* Sending in-memory messages via MicroProfile and Vert.x Event Bus

This workshop is for beginners and takes one hour.

*The intention of this workshop is not to explain every aspect of reactive programming, but to explain core reactive principles and to deploy a complete reactive application which you can inspect after the workshop in more detail.*

## Get Started

These are the labs of this workshop, go through all of them in sequence, start with lab 1:

* Lab 1: [Create your OpenShift Environment](labs/lab1.md)
* Lab 2: [Deploy Kafka via Script](labs/lab2.md)
* Lab 3: [Deploy Postgres via Operator](labs/lab3.md)
* Lab 4: [Deploy Sample Application](labs/lab4.md)
* Lab 5: [Reactive Messaging with MicroProfile](labs/lab5.md)
* Lab 6: [Server Sent Events](labs/lab6.md)
* Lab 7: [Vert.x Event Bus](labs/lab7.md)
* Lab 8 (optional): [Use distributed Logging](labs/lab8.md)

## What to do next

The [blogs](https://github.com/IBM/cloud-native-starter/tree/master/reactive#blogs) as well as the [presentation](images/ReactiveMicroservices.pdf) describe the functionality in more detail.

There is a second workshop which uses the same sample application. That workshop is called [Reactive Endpoints with Quarkus on OpenShift](https://nheidloff.github.io/workshop-quarkus-openshift-reactive-messaging/) and it focusses on reactive APIs and API invocations. 