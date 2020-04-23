# Workshop: Reactive Messaging with Quarkus on OpenShift

In this workshop you'll learn how to implement reactive messaging functionality with Java, Quarkus, Kafka, Vert.x and MicroProfile. 

The code is available as open source as part of the [Cloud Native Starter](https://github.com/IBM/cloud-native-starter/tree/master/reactive) project. 

One benefit of reactive models is the ability to update web applications by sending messages, rather than pulling for updates. This is more efficient and improves the user experience.

Articles can be created via REST API. The web application receives a notification and adds the new article to the page. The animation shows how curl requests are executed at the bottom which trigger updates to the web application at the top.

<kbd><img src="images/demo-1-video-small.gif" /></kbd>

The next diagram explains the flow between the different components and microservices. This workshop only uses the highlighted services.

The API client 'Submissions' triggers the REST API of the 'Articles' service to create new articles. The 'Articles' service sends a message to the 'Web-API' service via 'Kafka'. The 'Web-API' provides a streaming endpoint that the web application 'Web-App' consumes.

<kbd><img src="images/demo-1-small.png" /></kbd>

## Objectives

After you complete this workshop, you'll understand the following reactive functionality:
* Sending events from microservices to web applications via Server Sent Events
* Sending in-memory messages via MicroProfile
* Sending in-memory messages via Vertx event bus
* Sending and receiving Kafka messages via MicroProfile
* Sending Kafka messages via Kafka API

## Get Started

These are the labs of this workshop, go through all of them in sequence, start with lab 1:

- Lab 1: [Create your Cloud environment](labs/lab1.md)
- Lab 2: [to be done](labs/lab2.md)

## What to do next

The [presentation](images/ReactiveMicroservices.pdf) as well as the [blogs](https://github.com/IBM/cloud-native-starter/tree/master/reactive#blogs) describe the functionality in more detail.