# Push Notifications

*From: [Wikipedia](https://en.wikipedia.org/wiki/Push_technology)*

> A style of Internet-based communication where the request for a given transaction is initiated by the publisher or central server. It is contrasted with pull/get, where the request for the transmission of information is initiated by the receiver or client.

> Push services are often based on information preferences expressed in advance. This is called a [publish/subscribe model](../design/pub_sub.md). A client "subscribes" to various information "channels" provided by a server; whenever new content is available on one of those channels, the server pushes that information out to the client.

> Push is sometimes emulated with a polling technique, particularly under circumstances where a real push is not possible, such as sites with security policies that require rejection of incoming HTTP/S requests.

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [History](#history)
- [How do push notifications work?](#how-do-push-notifications-work)
	- [OS Push Services](#os-push-services)
- [APNS → App](#apns-app)
	- [iOS](#ios)
	- [Android](#android)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

## History

-   **2009:** Apple launches Apple Push Notification Service (APNS), the first push service.
-   **2010:** Google released its own service, Google Cloud to Device Messaging (C2DM).
-   **2013:** Google introduces "rich notifications". Rich notifications can contain images, as well as action buttons. Action buttons let users take immediate action from a notification. For example, the user can play a song, open the app, or see more information.
-   **2014:** Apple added interactive buttons. These buttons allow users to send a response right away to the app publisher. Shortly after, Apple extended push notifications to the Apple Watch.

## How do push notifications work?

There are three actors involved with delivering a push notification, along with a fourth, optional, component for advanced functionality.

1.  Operating system push notification service (OSPNS). Each mobile operating system (OS), including iOS, Android, Fire OS, Windows, and BlackBerry, has its own service.
1.  App publisher. The app publisher enables their app with an OSPNS. Then, the publisher uploads the app to the app store.
1.  Client app. This is an OS-specific app, installed on a user's device. It receives incoming notifications.
1.  (Optional) SDK (OS client library Software Development Kit). This is code installed in an app that enables extended segmentation and analytics capabilities.

![Push Flowchart](http://cdn3.raywenderlich.com/wp-content/uploads/2011/05/Push-Overview.jpg)

### OS Push Services

-   [Amazon Device Messaging](https://developer.amazon.com/public/apis/engage/device-messaging/tech-docs/01-understanding-adm)
-   [Apple Push Notification Service](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
-   [Google Cloud Messaging: Overview](https://developers.google.com/cloud-messaging/gcm)
-   [Windows Push Notification Service](https://msdn.microsoft.com/en-us/library/windows/apps/mt187203.aspx)

## APNS → App

### iOS

### Android

*From: [StackOverflow](http://stackoverflow.com/questions/11508613/how-does-push-notification-technology-work-on-android)*

> There is a TCP socket waiting in accept mode on a cloud Google server. The TCP connection had been initiated by the Goggle Play application. That's why Google Play must be installed on the device for making Google Cloud Messaging (GCM) (formerly Android Cloud to Device Messaging Service - C2DM) work.

> When this TCP client socket receives some message, the message contains information such as the package name of the application it should be addressed to, and of course - the data itself. This data is parsed and packed into an intent that is broadcast and eventually received by the application.

> The TCP socket stays open even when the device's radio state turns into "idle" mode. Applications don't have to be running to receive the intents.

---

## iOS vs Android

|                                 | iOS                      | Android     |
|---------------------------------|--------------------------|-------------|
| Opt-in require                  | true                     | false       |
| Payload limit                   | 2kb                      | 4kb         |
| Buttons                         | 2                        | 3           |
| Feedback                        | Via APNS Feedback Server | From Device |
| Direct app feedback on delivery | no                       | yes         |
| Two way messaging support       | No                       | Yes (XMPP)  |
| Multi-device Messaging          | No                       | Yes         |

## References

-   [Apple Push Notification Service](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
-   [Google Cloud Messaging: Overview](https://developers.google.com/cloud-messaging/gcm)
-   [StackOverflow: How does push notification technology work on Android?](http://stackoverflow.com/questions/11508613/how-does-push-notification-technology-work-on-android)
-   [StackOverflow: Send push message to multiple devices](http://stackoverflow.com/questions/7913995/send-push-message-to-multiple-devices)
-   [Understanding Amazon Device Messaging](https://developer.amazon.com/public/apis/engage/device-messaging/tech-docs/01-understanding-adm)
-   [Urban Airship: Push Notifications Explained](https://www.urbanairship.com/push-notifications-explained)
-   [Windows Push Notification Services (WNS) overview](https://msdn.microsoft.com/en-us/library/windows/apps/mt187203.aspx)
