Navigator:
* Lab 1: [Create your Cloud Environment](labs/lab1.md)
* Lab 2: [Deploy Kafka via Script](labs/lab2.md)
* Lab 3: [Deploy Postgres via Operator](labs/lab3.md)
* Lab 4: Deploy Sample Application

---

# Lab 3: Deploy Sample Application

In this lab you'll deploy the sample application which consists of three microservices and a web application.

### Step 1: Create Project

Invoke the following command in the Cloud Shell.

```
$ oc new-project cloud-native-starter
```

![kafka deployment](../images/deploy-app0.png)

### Step 2: Deploy Services and Web Application

Invoke the following command in the Cloud Shell.

```
$ os4-scripts/deploy-articles-reactive-postgres-via-oc.sh
```

![kafka deployment](../images/deploy-app1.png)

Invoke the following command in the Cloud Shell.

```
$ os4-scripts/deploy-authors-via-oc.sh
```

![kafka deployment](../images/deploy-app2.png)

Invoke the following command in the Cloud Shell.

```
$ os4-scripts/deploy-web-api-reactive-via-oc.sh
```

![kafka deployment](../images/deploy-app3.png)

Invoke the following command in the Cloud Shell.

```
$ os4-scripts/deploy-web-app-reactive-via-oc.sh
```

![kafka deployment](../images/deploy-app4.png)

### Step 3: Verify the Installation 

Make sure all four pods in the 'cloud-native-starter' project are running. Note that it takes a couple of minutes until this happens.

![kafka deployment](../images/verify-app1.png)

The previous steps have create build configs, builds and image streams.

![kafka deployment](../images/verify-app2.png)

![kafka deployment](../images/verify-app3.png)

![kafka deployment](../images/verify-app4.png)

---

__Continue with [Lab 5: to be done](lab5.md)__
