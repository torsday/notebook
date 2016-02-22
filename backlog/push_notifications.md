# Push Notifications

---

**Table of Contents**

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [History](#history)
- [How do push notifications work?](#how-do-push-notifications-work)
- [References](#references)

<!-- /TOC -->

---

## History

- June 2009: Apple launches Apple Push Notification Service (APNs), the first push service.
- May 2010: Google released its own service, Google Cloud to Device Messaging (C2DM).
- May 2013: Google introduces "rich notifications". Rich notifications can contain images, as well as action buttons. Action buttons let users take immediate action from a notification. For example, the user can play a song, open the app, or see more information.
- September 2014: Apple added interactive buttons. These buttons allow users to send a response right away to the app publisher. Shortly after, Apple extended push notifications to the Apple Watch.



## How do push notifications work?

There are three actors involved with delivering a push notification, along with a fourth, optional, component for advanced functionality.

1. Operating system push notification service (OSPNS). Each mobile operating system (OS), including iOS, Android, Fire OS, Windows, and BlackBerry, has its own service.
1. App publisher. The app publisher enables their app with an OSPNS. Then, the publisher uploads the app to the app store.
1. Client app. This is an OS-specific app, installed on a user's device. It receives incoming notifications.
1. (Optional) SDK (OS client library Software Development Kit). This is code installed in an app that enables extended segmentation and analytics capabilities.

![Push Flowchart](http://cdn3.raywenderlich.com/wp-content/uploads/2011/05/Push-Overview.jpg)


## References

* [Urban Airship: Push Notifications Explained](https://www.urbanairship.com/push-notifications-explained)
