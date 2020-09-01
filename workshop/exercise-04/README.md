# Exercise 4: Vert.x Event Bus

The [Vert.x Event Bus](https://vertx.io/docs/vertx-core/java/#event_bus) allows different parts of your application to communicate with each other. Check out the [guide](https://quarkus.io/guides/reactive-messaging) to find out more details.

In this lab you'll learn how to use the bus to communicate in-memory between different layers of the 'Articles' service.

![](../../images/event-bus1.png)

The 'Articles' service uses a clean architecture approach. There are three different layers:

* API
* Business
* Data

The API layer contains the implementation of the REST APIs and the external messaging interfaces. The data layer contains the implementation of the persistence and could include calls to other external services. The API layer and the data layer can be easily replaced without changing the business logic.

![](../../images/event-bus2.png)

In this lab you'll use the event bus to communicate between the business and the API layers.

### Step 1: Understand the Publisher

Let's take a look at the implementation of [ArticleService](https://github.com/IBM/cloud-native-starter/blob/master/reactive/articles-reactive/src/main/java/com/ibm/articles/business/ArticleService.java) in the business layer.

```
cd ~/cloud-native-starter/reactive/articles-reactive/src/main/java/com/ibm/articles/
cat business/ArticleService.java
```

![](../../images/event-bus3.png)

An instance of the bus can be injected via @Inject.

Next let's modify the method 'sendMessageToKafka' slightly by adding a System.out.println.

```
System.out.println("Sending message via Vert.x Event Bus");
```

```
cd ~/cloud-native-starter/reactive/articles-reactive/src/main/java/com/ibm/articles/
nano business/ArticleService.java
```

![](../../images/event-bus4.png)

Exit the Editor via 'Ctrl-X', 'y' and 'Enter'.

### Step 2: Understand the Subscriber

The method 'sendMessageToKafka' in the class [NewArticleCreatedListener.java](https://github.com/IBM/cloud-native-starter/blob/master/reactive/articles-reactive/src/main/java/com/ibm/articles/apis/NewArticleCreatedListener.java) in the API layer is invoked when the messages should be sent to Kafka. This is defined via the annotation @ConsumeEvent.

Let's modify this method slightly as well.

```java
System.out.println("Receiving message via Vert.x Event Bus");
```

```sh
cd ~/cloud-native-starter/reactive/articles-reactive/src/main/java/com/ibm/articles/
nano apis/NewArticleCreatedListener.java
```

![](../../images/event-bus5.png)

Exit the Editor via 'Ctrl-X', 'y' and 'Enter'.

### Step 3: Deploy new Version

```sh
cd ~/cloud-native-starter/reactive/articles-reactive
oc start-build articles-reactive --from-dir=.
```

![](../../images/event-bus6.png)

Wait until the build has been completed.

![](../../images/event-bus7.png)

Delete the articles pod. This will trigger Kubernetes to start a new pod with the latest version of the image.

![](../../images/event-bus8.png)

### Step 4: Deploy new Version

Create a new article by invoking a curl post command. You can get the URL from the script show-urls.

```sh
~/cloud-native-starter/reactive/os4-scripts/show-urls.sh
```

![](../../images/microprofile-kafka8.png)

In order to see the logs, you can do two things:

1. Use the following instructions which leverage a terminal
2. Use distributed logging as documented in [lab 8](lab8.md)

In the terminal get the pod name:

```sh
oc get pods
```

![](../../images/event-bus9.png)

After this invoke this command to display the logs of the pod.

```sh
oc logs articles-reactive-xxxxxxxxxxx-xxxxx
```

![](../../images/event-bus10.png)

Your added line shows up in the logs now.

