title: Push Notifications
author:
  name: Chris Torstenson
output: push_notifications_prez.html

--

# Push Notifications

## An Overview

---

### Publish–subscribe pattern

-   A client "subscribes" to various information "channels" provided by a server; whenever new content is available on one of those channels, the server pushes that information out to the client.
-   Publisher & Subscriber don't have to know about each other, just the classes on creates and the other has an interest in.

---

### History

-   **2009:**  launches Apple Push Notification Service (APNs)
-   **2010:** Google releases it's own service, now called Google Cloud Messaging
-   **2013:** Google introduces "rich notifications": (buttons/images)
-   **2014:** Apple adds interactive buttons + brings notifications to  Watch

---

### Basics

#### Operating System Push Notification service *(OSPNs)*

Each mobile OS has its own service:

-   Amazon Device Messaging
-   Apple Push Notification Service
-   BlackBerry
-   Google Cloud Messaging
-   Windows Push Notification Service

---

### How do push notifications work?

delivery:

[Push Flowchart](http://cdn3.raywenderlich.com/wp-content/uploads/2011/05/Push-Overview.jpg)

---

### Android

-   There is a TCP socket waiting in accept mode on a cloud Google server.
-   When this TCP client socket receives some message, the message contains information such as the package name of the application it should be addressed to, and the data itself. This data is parsed and packed into an intent that is broadcast and eventually received by the application.
-   The TCP socket stays open even when the device's radio state turns into "idle" mode. Applications don't have to be running to receive the intents.

---

### iOS  Token Generation and Dispersal

> An app must register with the system to receive remote notifications. Upon receiving a registration request, the system forwards the request to APNs, which generates a unique device token, for the app, using information contained in the device’s certificate. It then encrypts the token using a token key and returns it to the device, as shown in Figure 3-5. The system delivers the device token to your app as an NSData object. Upon receiving this token, your app must forward it to your provider in either binary or hexadecimal format. Your provider cannot send notifications to the device without this token.

*Note: A **device token** is not a unique ID that you can use to identify a device. Device tokens can change after updating the operating system on a device. As a result, apps should send their device token.*

[APNs Token Generation & Dispersal](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_generation_2x.png)

---

### Token Trust (Notification)

> Every notification that your provider sends to APNs must be accompanied by the device token associated of the device for which the notification is intended. APNs decrypts the token using its token key to ensure the validity of the notification source—that is, your provider. APNs uses the device ID contained in the device token to determine the identity of the target device. It then sends the notification to that device

[Notification Diagram](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_trust_2x.png)

---

### iOS vs Android

|                              |           iOS            |   Android   |
|------------------------------|:------------------------:|:-----------:|
| **Opt-in require**           |            ✓             |             |
| **Payload limit**            |           2kb            |     4kb     |
| **Buttons**                  |            2             |      3      |
| **Feedback**                 | Via APNs Feedback Server | From Device |
| **App feedback on delivery** |                          |      ✓      |
| **Multi-device Messaging**   |                          |      ✓      |
