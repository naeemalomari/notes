# Read: 26 - [Android Fundamentals](https://developer.android.com/guide/components/fundamentals)

- Android apps can be written using Kotlin, Java, and C++ languages.

- Each Android app, protected by the following Android security features:

1. The Android operating system is a multi-user Linux system in which each app is a different user.
2. By default, the system assigns each app a unique Linux user ID (the ID is used only by the system and is unknown to the app). The system sets permissions for all the files in an app so that only the user ID assigned to that app can access them.
3. Each process has its own virtual machine (VM), so an app's code runs in isolation from other apps.
4. By default, every app runs in its own Linux process. The Android system starts the process when any of the app's components need to be executed, and then shuts down the process when it's no longer needed or when the system must recover memory for other apps.

- The Android system implements the principle of least privilege. That is, each app, by default, has access only to the components that it requires to do its work and no more.

- It's possible to arrange for two apps to share the same Linux user ID, in which case they are able to access each other's files.

- An app can request permission to access device data. The user has to explicitly grant these permissions.

## App components

### There are four different types of app components

1. **Activities**

- Is the entry point for interacting with the user.
- It represents a single screen with a user interface.

2. **Services**

- Is a general-purpose entry point for keeping an app running in the background for all kinds of reasons.
- It is a component that runs in the background to perform long-running operations or to perform work for remote processes.
- A service does not provide a user interface.

- 1. Started services tell the system to keep them running until their work is completed.
And it might be Syncing data in the background or playing music:
- Music playback is something the user is directly aware of and he can stop it whenever he wants, the app tells the system this by saying it wants to be foreground with a notification to tell the user about it.

- A regular background service is not something the user is directly aware as running, so the system has more freedom in managing its process.

- 2. Bound services run because some other app (or the system) has said that it wants to make use of the service. This is basically the service providing an API to another process.

- A service is implemented as a subclass of Service.

3. Broadcast receivers

- Is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements.
- Because broadcast receivers are another well-defined entry into the app, the system can deliver broadcasts even to apps that aren't currently running.

- A broadcast receiver is implemented as a subclass of BroadcastReceiver and each broadcast is delivered as an Intent object.

4. Content providers

- A content provider manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access.
- Through the content provider, other apps can query or modify the data if the content provider allows it.

There are a few particular things this allows the system to do in managing an app:

- 1. Assigning a URI doesn't require that the app remain running, so URIs can persist after their owning apps have exited. The system only needs to make sure that an owning app is still running when it has to retrieve the app's data from the corresponding URI.
- 2. These URIs also provide an important fine-grained security model.

- Content providers are also useful for reading and writing data that is private to your app and not shared.

- A content provider is implemented as a subclass of ContentProvider and must implement a standard set of APIs that enable other apps to perform transactions. For more information, see the Content Providers developer guide.

- A unique aspect of the Android system design is that any app can start another app’s component.

---

## Activating components

- Three of the four component types—activities, services, and broadcast receivers—are activated by an asynchronous message called an intent.
- Intents bind individual components to each other at runtime. You can think of them as the messengers that request an action from other components, whether the component belongs to your app or another.
- An intent is created with an Intent object, which defines a message to activate either a specific component (explicit intent) or a specific type of component (implicit intent).

There are separate methods for activating each type of component:

- 1. You can start an activity or give it something new to do by passing an Intent to `startActivity()` or `startActivityForResult()` (when you want the activity to return a result).
- 2. With Android 5.0 (API level 21) and later, you can use the `JobScheduler` class to schedule actions. For earlier Android versions, you can start a service (or give new instructions to an ongoing service) by passing an Intent to startService(). You can bind to the service by passing an Intent to bindService().
- 3. You can initiate a broadcast by passing an Intent to methods such as `sendBroadcast(), sendOrderedBroadcast(), or sendStickyBroadcast()`.
- 4. You can perform a query to a content provider by calling `query()` on a ContentResolver.

---

## The manifest file

- Before the Android system can start an app component, the system must know that the component exists by reading the app's manifest file, `AndroidManifest.xml`.

- The manifest does a number of things in addition to declaring the app's components, such as the following:

- 1. Identifies any user permissions the app requires, such as read-access to the user's contacts.
- 2. Declares the minimum API Level required by the app.
- 3. Declares hardware and software features used or required by the app, such as a camera.
- 4. Declares API libraries the app needs to be linked against, such as the Google Maps library.

---

## App resources

- For every resource that you include in your Android project, the SDK build tools define a unique integer ID, which you can use to reference the resource from your app code or from other resources defined in XML.
For example, if your app contains an image file named logo.png (saved in the res/drawable/ directory), the SDK tools generate a resource ID named R.drawable.logo. This ID maps to an app-specific integer, which you can use to reference the image and insert it in your user interface.
