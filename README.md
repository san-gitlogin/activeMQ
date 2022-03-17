# Active MQ - Local machine JMS Point to Point and Publisher Subscriber model | Windows 11
Demonstration on the working of ActiveMQ JMS (Java Message Service) methods using Java JFrame. The application is designed to understand the working of point to point and publisher subscriber model of JMS using active mq server.

# Java Application

![Screenshot 2022-03-17 223530](https://user-images.githubusercontent.com/9679358/158855140-051aba22-d42d-4fc6-bfd3-fd61f361d4df.png)

# Steps to execute:

Step 1: Activate ActiveMQ - Download ActiveMQ from https://activemq.apache.org/components/classic/download/ and under bin folder run "/win32/activemq.bat" or "/win64/activemq.bat" based on your operating system. Once the command prompt returns the following message, you can proceed on working with JMS models.

![Screenshot 2022-03-17 224026](https://user-images.githubusercontent.com/9679358/158857461-aa600a5b-5801-48b5-a1f7-fb9ddd6a6524.png)

Note: ActiveMQ version 5.16.4 is used in this project.

Step 2: Open web browser and navigate to "http://localhost:8161/admin". Username and Password is "admin". Once logged in, you will be able to see ActiveMQ console where you will be able to track the information on Topics, Active subscribers, Queueing of messages etc.,

![Screenshot 2022-03-17 224625](https://user-images.githubusercontent.com/9679358/158857490-a22c1f29-dd7b-40d9-bbe3-d974f5917df1.png)

Step 3: NetBeans IDE is used for better visualization of the application using JFrame. Get the NetBeans IDE from "https://netbeans.apache.org/download/index.html".

Step 4: Download the project files. If necessary, replace the file "san_activemq\lib\activemq-all-5.16.4.jar" with latest "activemq-all-<latest version>.jar" file version you need. 

Step 5: Open san_activemq\src\activeMQJFrame\MainFrame.java using NetBeans IDE and Run the project.

Note: ActiveMQ must be running at the background to successfully send or receive messages.

# Working:

Point to Point model : 
  
Refer "sendP2PActionPerformed" and "activateReceiverActionPerformed" in MainFrame.java
  
 The message sent by the "point to point" sender is enqueued into the Queue. The message can only be received by an receiver, if the receiver holds the same "Service name" as the sender. Once a receiver with same service name is activated, the message is dequeued from the queue and the receiver receives the message.
  
Under Sender Tab -> Point to Point -> Enter the message you would need to send (Remember the service name is "Queue") -> Hit "Send Message".

![image](https://user-images.githubusercontent.com/9679358/158863522-28cf4cbb-5fc8-4413-b53d-b558af6e9814.png)

In the output menu in Netbeans -> It must look something like this ->
  ![image](https://user-images.githubusercontent.com/9679358/158863746-aa6928f8-e260-47a9-a05b-4ce230647374.png)

Now under Receiver Tab -> Point to Point -> Activate Receiver (Remember the receiver also holds the same service name "Queue")
  
  ![image](https://user-images.githubusercontent.com/9679358/158864065-74cef2a7-34df-403c-bb4b-bdf8369e7a50.png)
  
Note: In Point to Point method, the receiver need not be in active state to receive messages, as the message is available in the queue that is later sent once the receiver gets activated. It is not the same sceenario in Publisher subscriber model.
  
Publisher Subscriber model :

Refer "subscribeAndActivateActionPerformed" and "sendSubMessageActionPerformed" in MainFrame.java

  For Subscription model, there will be many users subscribed to a topic with which they receive messages. Similar to how we receive mails from promotional websites, we are the subscribers who might have subscribed to receive updates from the promotional websites such as Job updates.
  
  Under Receiver tab -> Subscription -> Enter the User name and Topic to which they are interested to receive messages on -> Hit "Subscribe"
  (The User and his interest of Topic is added into the activeMQ server)
  
  ![image](https://user-images.githubusercontent.com/9679358/158864981-1c013011-3696-4ac1-b157-e18c753b0cda.png)

  Under Sender tab -> Subscription -> Enter the Topic name with which the sender needs to send messages -> Enter the message you need to send to users interested in that particular topic -> Hit "Send Message"
  
  ![image](https://user-images.githubusercontent.com/9679358/158865475-13cc42df-1bab-4196-ac90-c8515538115c.png)

  You can notice that there are two users, who are Subscribed to topic named "VIT". As soon as the sender sends a message for users subscribed to the particular topic, the subscribers receive message.
  
  Note: In Publisher Subscriber model, the subscribers need to be in active state to receive messages. In this application, as soon as there is user subscribing to a particular topic, they are in active state. That is how, the received messages for actively subscribed users are stacked in the tabular column.
  
Sample Screenshot : 
  
  ![image](https://user-images.githubusercontent.com/9679358/158866616-42dfa6df-7645-4c60-a3d3-881a4a972053.png)

Other Reference :
https://www.tomitribe.com/blog/5-minutes-or-less-activemq-with-jms-queues-and-topics/
  
