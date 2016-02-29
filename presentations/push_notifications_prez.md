title: Push Notifications
author:
  name: Chris Torstenson
output: push_notifications_prez.html

--

# Push Notifications

## An Overview

---

### History

-   **2009:**  launches Apple Push Notification Service
-   **2010:** Google Launches Google Cloud Messaging
-   **2013:** Google adds buttons & images
-   **2014:** Apple adds buttons

---

### Publish–subscribe pattern

-   A client "subscribes" to various information "channels" provided by a server; whenever new content is available on one of those channels, the server pushes that information out to the client.
-   Publisher & Subscriber don't have to know about each other, just the classes the former creates and the latter has an interest in.

---

### Sockets

-   There is a TCP socket waiting in accept mode on a cloud server.
-   When this TCP client socket receives some message (from the app's server), the data is parsed and packed into an intent that is broadcast and eventually received by the application.
-   The TCP socket stays open even when the device's radio state turns into "idle" mode. Applications don't have to be running to receive the intents.

---

### Heartbeat

-   If the connection is dropped but the device doesn't know it, it'll wait until it does a heartbeat and realizes the connection is closed.

---

### Flow Charts

-   [Notification Diagram](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_trust_2x.png)
-   [Message](http://patentimages.storage.googleapis.com/US20140066063A1/US20140066063A1-20140306-D00005.png)

---

### Token Generation and Dispersal

1.  An *app* must register with the system to receive remote notifications.
2.  Upon receiving a registration request, the system forwards the request to the notifications server, which generates a *unique device token*, for the app, using information contained in the *device’s* certificate.
3.  It then encrypts the token using a token key and returns it to the device.
4.  Upon receiving this token, your app must forward it to the *app's server*.

---

*Note: A **device token** is not a unique ID that you can use to identify a device. Device tokens can change after updating the operating system on a device. As a result, apps should send their device token.*

---

### Token Trust (Notification)

1.  Every notification that your provider sends to APNs must be accompanied by the device token associated of the device for which the notification is intended.
1.  APNs decrypts the token using its token key to ensure the validity of the notification source—that is, your provider.
1.  APNs uses the device ID contained in the device token to determine the identity of the target device.
1.  It then sends the notification to that device

---

### Flow Charts

-   [APNs Token Generation & Dispersal](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_generation_2x.png)

---

### Operating System Push Notification service *(OSPNs)*

Each mobile OS has its own service:

-   Amazon Device Messaging
-   Apple Push Notification Service
-   BlackBerry
-   Google Cloud Messaging
-   Windows Push Notification Service

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

---

### Flow Chart

-   [Complete Notification Diagram](http://cdn3.raywenderlich.com/wp-content/uploads/2011/05/Push-Overview.jpg)
