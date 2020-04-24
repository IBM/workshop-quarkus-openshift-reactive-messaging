Navigator:
* Lab 1: [Create your Cloud Environment](labs/lab1.md)
* Lab 2: [Deploy Kafka via Script](labs/lab2.md)
* Lab 3: Deploy Postgres via Operator
* Lab 4: [Deploy Sample Application](labs/lab4.md)

---

# Lab 3: Deploy Postgres via Operator

In this lab you'll deploy Postgres and set up a database which is used by the 'Articles' service.

### Step 1: Create Project

In the Cloud Shell enter the following command.

```
$ oc new-project postgres
```

![kafka deployment](../images/setup-postgres1.png)

### Step 2: Install the Postgres Operator

Open the OperatorHub page and filter by 'postgres'. Open the operator 'PostgreSQL Operator by Dev4devs.com'.

![kafka deployment](../images/setup-postgres2.png)

Click 'Install'.

![kafka deployment](../images/setup-postgres3.png)

Create a subscription. Make sure your new project 'postgres' is selected in the combobox.

![kafka deployment](../images/setup-postgres4.png)

### Step 3: Create the Database

Click on the operator.

![kafka deployment](../images/setup-postgres5.png)

Click on 'Create Instance' in the 'Database Database' box.

![kafka deployment](../images/setup-postgres6.png)

Edit the yaml. The database name needs to be changed to  'database-articles'. The namespace should be 'postgres' by default. After this click 'Create'.

![kafka deployment](../images/setup-postgres7.png)

### Step 4: Verify the Installation 

From the 'Projects' page open 'postgres'.

![kafka deployment](../images/setup-postgres8.png)

Click on '2 Pods'.

![kafka deployment](../images/setup-postgres9.png)

Make sure the pod 'database-articles....' is running.

![kafka deployment](../images/setup-postgres10.png)

---

__Continue with [Lab 4: Deploy Sample Application](lab4.md)__
