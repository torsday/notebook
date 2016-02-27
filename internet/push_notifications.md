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
- [Android](#android)
- [iOS](#ios)
	- [Token Generation and Dispersal](#token-generation-and-dispersal)
	- [Token Trust (Notification)](#token-trust-notification)
- [iOS vs Android](#ios-vs-android)
- [Examples](#examples)
	- [Pushing to a single device from Provider in PHP](#pushing-to-a-single-device-from-provider-in-php)
- [References](#references)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---


## History

-   **2009:** Apple launches Apple Push Notification Service (APNs), the first push service.
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

## Android

*From: [StackOverflow](http://stackoverflow.com/questions/11508613/how-does-push-notification-technology-work-on-android)*

> There is a TCP socket waiting in accept mode on a cloud Google server. The TCP connection had been initiated by the Goggle Play application. That's why Google Play must be installed on the device for making Google Cloud Messaging (GCM) (formerly Android Cloud to Device Messaging Service - C2DM) work.

> When this TCP client socket receives some message, the message contains information such as the package name of the application it should be addressed to, and of course - the data itself. This data is parsed and packed into an intent that is broadcast and eventually received by the application.

> The TCP socket stays open even when the device's radio state turns into "idle" mode. Applications don't have to be running to receive the intents.

---

## iOS

### Token Generation and Dispersal

> An app must register with the system to receive remote notifications, as described in [Registering for Remote Notifications](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/IPhoneOSClientImp.html#//apple_ref/doc/uid/TP40008194-CH103-SW2). Upon receiving a registration request, the system forwards the request to APNs, which generates a unique device token, for the app, using information contained in the device’s certificate. It then encrypts the token using a token key and returns it to the device, as shown in Figure 3-5. The system delivers the device token to your app as an NSData object. Upon receiving this token, your app must forward it to your provider in either binary or hexadecimal format. Your provider cannot send notifications to the device without this token.

*Note: A **device token** is not a unique ID that you can use to identify a device. Device tokens can change after updating the operating system on a device. As a result, apps should send their device token.*

![APNs Token Generation & Dispersal](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_generation_2x.png)

### Token Trust (Notification)

> Every notification that your provider sends to APNs must be accompanied by the device token associated of the device for which the notification is intended. APNs decrypts the token using its token key to ensure the validity of the notification source—that is, your provider. APNs uses the device ID contained in the device token to determine the identity of the target device. It then sends the notification to that device

![Notification Diagram](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Art/token_trust_2x.png)

---

## iOS vs Android

|                                 |           iOS            |   Android   |
|---------------------------------|:------------------------:|:-----------:|
| Opt-in require                  |           true           |    false    |
| Payload limit                   |           2kb            |     4kb     |
| Buttons                         |            2             |      3      |
| Feedback                        | Via APNs Feedback Server | From Device |
| Direct app feedback on delivery |            no            |     yes     |
| Two way messaging support       |            No            | Yes (XMPP)  |
| Multi-device Messaging          |            No            |     Yes     |

---

## Examples

### Pushing to a single device from Provider in PHP

```php
$deviceToken = 'de641706f194fa32169dcd8297309153bb6b4de838f9b7cb7cb83c0e24b6609b';

// Put your private key's passphrase here:
$passphrase = 'ibpspass';

// Put your alert message here:
$message = 'New promotion is updated!';

// ---

$ctx = stream_context_create();
stream_context_set_option($ctx, 'ssl', 'local_cert', 'ck.pem');
stream_context_set_option($ctx, 'ssl', 'passphrase', $passphrase);

// Open a connection to the APNs server
$fp = stream_socket_client(
    'ssl://gateway.sandbox.push.apple.com:2195', $err,
    $errstr, 60, STREAM_CLIENT_CONNECT|STREAM_CLIENT_PERSISTENT, $ctx);

if (!$fp)
    exit("Failed to connect: $err $errstr" . PHP_EOL);

echo 'Connected to APNs' . PHP_EOL;

// Create the payload body
$body['aps'] = array(
    'alert' => $message,
    'sound' => 'default'
    );

// Encode the payload as JSON
$payload = json_encode($body);

// Build the binary notification
$msg = chr(0) . pack('n', 32) . pack('H*', $deviceToken) . pack('n', strlen($payload)) . $payload;

// Send it to the server
$result = fwrite($fp, $msg, strlen($msg));

if (!$result)
    echo 'Message not delivered' . PHP_EOL;
else
    echo 'Message successfully delivered' . PHP_EOL;

// Close the connection to the server
fclose($fp);
```

---

## References

-   [Apple Push Notification Service](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html)
-   **[Apple: Local and Remote Notification Programming Guide](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html#//apple_ref/doc/uid/TP40008194-CH100-SW1)**
-   [Google Cloud Messaging: Overview](https://developers.google.com/cloud-messaging/gcm)
-   [StackOverflow: How does push notification technology work on Android?](http://stackoverflow.com/questions/11508613/how-does-push-notification-technology-work-on-android)
-   [StackOverflow: Send push message to multiple devices](http://stackoverflow.com/questions/7913995/send-push-message-to-multiple-devices)
-   [Understanding Amazon Device Messaging](https://developer.amazon.com/public/apis/engage/device-messaging/tech-docs/01-understanding-adm)
-   [Urban Airship: Push Notifications Explained](https://www.urbanairship.com/push-notifications-explained)
-   [Windows Push Notification Services (WNS) overview](https://msdn.microsoft.com/en-us/library/windows/apps/mt187203.aspx)
