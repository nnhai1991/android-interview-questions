

### Core Android

#### Base

* Tell all the Android application components. [Android Official](https://developer.android.com/guide/components/fundamentals.html#Components)
    - There are four different types of app components:
        - Activities
        - Services
        - Broadcast receivers
        - Content providers

* What is the structure of an Android Application?

* What is `Context`? How is it used? [MindOrks](https://blog.mindorks.com/understanding-context-in-android-application-330913e32514)
    - As the name suggests, it's the context of current state of the application/object. It lets newly-created objects understand what has been going on. Typically you call it to get information regarding another part of your program (activity and package/application).
    - And also, Context is a handle to the system, it provides services like resolving resources, obtaining access to databases and preferences, and so on. An Android app has activities. It’s like a handle to the environment your application is currently running in. The activity object inherits the Context object. It allows access to application specific resources and class and information about the application environment.
    - You can get the context by invoking getApplicationContext(), getContext(), getBaseContext() or this (when in a class that extends from Context, such as the Application, Activity, Service and IntentService classes).

* What is `AndroidManifest.xml`? [Android Official](https://developer.android.com/guide/topics/manifest/manifest-intro)
    - Every app project must have an AndroidManifest.xml file (with precisely that name) at the root of the project source set. The manifest file describes essential information about your app to the Android build tools, the Android operating system, and Google Play.
* What is `Application` class?
    - Base class for maintaining global application state. You can provide your own implementation by creating a subclass and specifying the fully-qualified name of this subclass as the "android:name" attribute in your AndroidManifest.xml's <application> tag. The Application class, or your subclass of the Application class, is instantiated before any other class when the process for your application/package is created. 
#### Activity

* What is `Activity`? [MindOrks](https://blog.mindorks.com/android-activity-lifecycle)
    - An activity is the entry point for interacting with the user. It represents a single screen with a user interface
    -  An activity facilitates the following key interactions between system and app:
        - Keeping track of what the user currently cares about (what is on screen) to ensure that the system keeps running the process that is hosting the activity.
        - Knowing that previously used processes contain things the user may return to (stopped activities), and thus more highly prioritize keeping those processes around.
        - Helping the app handle having its process killed so the user can return to activities with their previous state restored.
        - Providing a way for apps to implement user flows between each other, and for the system to coordinate these flows. (The most classic example here being share.)

* Explain `Activity` and `Fragment` lifecycle. (Complete diagram [GitHub](https://github.com/xxv/android-lifecycle), simplified diagram for [Activity](https://developer.android.com/guide/components/activities/activity-lifecycle.html#alc), [Fragment](https://developer.android.com/guide/components/fragments.html#Lifecycle)), [Activity lifecycle](https://blog.mindorks.com/android-activity-lifecycle) and [Fragments lifecycle](https://blog.mindorks.com/android-fragments-and-its-lifecycle)

* What are "launch modes"? [MindOrks](https://blog.mindorks.com/android-activity-launchmode-explained-cbc6cf996802)
    - Launch modes allow you to define how a new instance of an activity is associated with the current task. You can define different launch modes in two ways:
  
        - Using the manifest file: When you declare an activity in your manifest file, you can specify how the activity should associate with tasks when it starts.
        - Using Intent flags: When you call startActivity(), you can include a flag in the Intent that declares how (or whether) the new activity should associate with the current task.
    - A task is a collection of activities that users interact with when performing a certain job. The activities are arranged in a stack—the back stack)—in the order in which each activity is opened
  
#### Fragments

* What is `Fragment`? [MindOrks](https://blog.mindorks.com/android-fragments-and-its-lifecycle)
    - A Fragment represents a behavior or a portion of user interface in a FragmentActivity. You can combine multiple fragments in a single activity to build a multi-pane UI and reuse a fragment in multiple activities. You can think of a fragment as a modular section of an activity, which has its own lifecycle, receives its own input events, and which you can add or remove while the activity is running (sort of like a "sub activity" that you can reuse in different activities).
* What is the difference between a `Fragment` and an `Activity`? Explain the relationship between the two.

* Why is it recommended to use only the default constructor to create a `Fragment`? [StackOverflow](https://stackoverflow.com/a/16042750/2809326)
    - The reason why you should be passing parameters through bundle is because when the system restores a fragment (e.g on config change), it will automatically restore your bundle.

    - The callbacks like onCreate or onCreateView should read the parameters from the bundle - this way you are guaranteed to restore the state of the fragment correctly to the same state the fragment was initialised with 
  
* How would you communicate between two Fragments? [Android Official](https://developer.android.com/training/basics/fragments/communicating.html)
    - Often you will want one Fragment to communicate with another, for example to change the content based on a user event. All Fragment-to-Fragment communication is done either through a shared ViewModel or through the associated Activity. Two Fragments should never communicate directly.

* What is retained `Fragment`? [AndroidDesignPatterns](https://www.androiddesignpatterns.com/2013/04/retaining-objects-across-config-changes.html)
    - setRetainInstance(true): The Fragment's state will be retained (and not destroyed!) across configuration changes (e.g. screen rotate). The state will be retained even if the configuration change causes the "parent" Activity to be destroyed. However, the view of the Fragment gets destroyed!


#### Views and ViewGroups

* What is `View` in Android? [MindOrks](https://blog.mindorks.com/android-user-interface-view-components)
    - View is a basic building block of UI (User Interface) in android. A view is a small rectangular box which responds to user inputs
    
* Difference between `View.GONE` and `View.INVISIBLE`? [StackOverflow](https://stackoverflow.com/questions/11556607/android-difference-between-invisible-and-gone)
    - View.INVISIBLE: This view is invisible, but it still takes up space for layout purposes.
    - View.GONE: This view is invisible, and it doesn't take any space for layout purposes.

* Can you create custom views? How? [MindOrks](https://blog.mindorks.com/create-your-own-custom-view)

    - Extend an existing View class or subclass with your own class.
    - Override some of the methods from the superclass. The superclass methods to override start with 'on', for example, onDraw(), onMeasure(), and onKeyDown(). This is similar to the on... events in Activity or ListActivity that you override for lifecycle and other functionality hooks.
    - Use your new extension class. Once completed, your new extension class can be used in place of the view upon which it was based.

* What are ViewGroups and how they are different from the Views?
    - ViewGroup is a invisible container of other views (child views) and other viewgroups
    
* What is a canvas?
  - The Canvas class holds the "draw" calls. To draw something, you need 4 basic components: A Bitmap to hold the pixels, a Canvas to host the draw calls (writing into the bitmap), a drawing primitive (e.g. Rect, Path, text, Bitmap), and a paint (to describe the colors and styles for the drawing). 

* What is a `SurfaceView`?
    - A SurfaceView is a special implementation of View that also creates its own dedicated Surface for the application to directly draw into (outside of the normal view hierarchy, which otherwise must share the single Surface for the window). 
* Relative Layout vs Linear Layout. [MindOrks](https://blog.mindorks.com/android-layout-relative-linear-frame)
    - LinearLayout means you can align views one by one (vertically/ horizontally).

    - RelativeLayout means based on relation of views from its parents and other views.

    - ConstraintLayout is similar to a RelativeLayout in that it uses relations to position and size widgets, but has additional flexibility and is easier to use in the Layout Editor.

    - WebView to load html, static or dynamic pages.

    - FrameLayout to load child one above another, like cards inside a frame, we can place one above another or anywhere inside the frame.
* Tell about Constraint Layout [MindOrks](https://blog.mindorks.com/using-constraint-layout-in-android-531e68019cd)
    - ConstraintLayout allows you to create large and complex layouts with a flat view hierarchy (no nested view groups). It's similar to RelativeLayout in that all views are laid out according to relationships between sibling views and the parent layout, but it's more flexible than RelativeLayout and easier to use with Android Studio's Layout Editor
* Do you know what is the view tree? How can you optimize its depth?
    - Use Hierarchy Viewer and Lint to examine and optimize your layout.
#### Displaying Lists of Content

* What is the difference between `ListView` and `RecyclerView`?
RecyclerView was created as a ListView improvement, so yes, you can create an attached list with ListView control, but using RecyclerView is easier as it:

    - Reuses cells while scrolling up/down - this is possible with implementing View Holder in the ListView adapter, but it was an optional thing, while in the RecycleView it's the default way of writing adapter.

    - Decouples list from its container - so you can put list items easily at run time in the different containers (linearLayout, gridLayout) with setting LayoutManager.

    - Animates common list actions - Animations are decoupled and delegated to ItemAnimator.

    - So, to conclude, RecyclerView is a more flexible control for handling "list data" that follows patterns of delegation of concerns and leaves for itself only one task - recycling items.
	
* What is the ViewHolder pattern? Why should we use it?
    - The views in the list are represented by view holder objects. These objects are instances of a class you define by extending RecyclerView.ViewHolder. Each view holder is in charge of displaying a single item with a view
    - The view holder objects are managed by an adapter, which you create by extending RecyclerView.Adapter. The adapter creates view holders as needed. The adapter also binds the view holders to their data. It does this by assigning the view holder to a position, and calling the adapter's onBindViewHolder() method. That method uses the view holder's position to determine what the contents should be, based on its list position. 
    - The RecyclerView creates only as many view holders as are needed to display the on-screen portion of the dynamic content, plus a few extra. As the user scrolls through the list, the RecyclerView takes the off-screen views and rebinds them to the data which is scrolling onto the screen. 

  * What is `SnapHelper`? [MindOrks](https://blog.mindorks.com/using-snaphelper-in-recyclerview-fc616b6833e8)

#### Dialogs and Toasts

* What is `Dialog` in Android?
    - A dialog is a small window that prompts the user to make a decision or enter additional information. A dialog does not fill the screen and is normally used for modal events that require users to take an action before they can proceed
* What is `Toast` in Android?
    - A toast provides simple feedback about an operation in a small popup. It only fills the amount of space required for the message and the current activity remains visible and interactive. Toasts automatically disappear after a timeout.
* What the difference between `Dialog` and `Dialog Fragment`?
    - A DialogFragment is a fragment that displays a dialog window, floating on top of its activity's window. This fragment contains a Dialog object, which it displays as appropriate based on the fragment's state. Control of the dialog (deciding when to show, hide, dismiss it) should be done through the API here, not with direct calls on the dialog.
    - Using DialogFragment to manage the dialog ensures that it correctly handles lifecycle events such as when the user presses the Back button or rotates the screen. The DialogFragment class also allows you to reuse the dialog's UI as an embeddable component in a larger UI, just like a traditional Fragment (such as when you want the dialog UI to appear differently on large and small screens).


#### Intents and Broadcasting

* What is `Intent`? [StackOverflow](https://stackoverflow.com/questions/6578051/what-is-an-intent-in-android)
    - An Intent is a messaging object you can use to request an action from another app component. Although intents facilitate communication between components in several ways, there are three fundamental use cases:
        - Starting an activity
        - Starting a service
        - Delivering a broadcast

* What is an Implicit `Intent`?
    - Explicit intents specify which application will satisfy the intent, by supplying either the target app's package name or a fully-qualified component class name. You'll typically use an explicit intent to start a component in your own app, because you know the class name of the activity or service you want to start. For example, you might start a new activity within your app in response to a user action, or start a service to download a file in the background.

* What is an Explicit `Intent`?
    - Implicit intents do not name a specific component, but instead declare a general action to perform, which allows a component from another app to handle it. For example, if you want to show the user a location on a map, you can use an implicit intent to request that another capable app show a specified location on a map.

* What is a `BroadcastReceiver`? [StackOverflow](https://stackoverflow.com/questions/5296987/what-is-broadcastreceiver-and-when-we-use-it)
    - A broadcast receiver is a component that responds to system-wide broadcast announcements. Many broadcasts originate from the system—for example, a broadcast announcing that the screen has turned off, the battery is low, or a picture was captured. Applications can also initiate broadcasts—for example, to let other applications know that some data has been downloaded to the device and is available for them to use. Although broadcast receivers don't display a user interface, they may create a status bar notification to alert the user when a broadcast event occurs. More commonly, though, a broadcast receiver is just a "gateway" to other components and is intended to do a very minimal amount of work. For instance, it might initiate a service to perform some work based on the event.

    - A broadcast receiver is implemented as a subclass of BroadcastReceiver and each broadcast is delivered as an Intent object. For more information, see the BroadcastReceiver class.
* What is a `LocalBroadcastManager`? [Developer Android](https://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)

* What is the function of an `IntentFilter`?
    - An intent filter is an expression in an app's manifest file that specifies the type of intents that the component would like to receive. For instance, by declaring an intent filter for an activity, you make it possible for other apps to directly start your activity with a certain kind of intent. Likewise, if you do not declare any intent filters for an activity, then it can be started only with an explicit intent.

* What is a Sticky `Intent`? [AndroidInterview](http://www.androidinterview.com/what-is-a-sticky-intent/)
    - Sticky Intent is also a type of Intent which allows a communication between function and a service sendStickyBroadcast() performs a sendBroadcast(Inent) know as sticky,the Intent your are sending stays around after the broadcast is complete, so that others can quickly retrieve that data through the return value of registerReceiver(BroadcastReceiver, IntentFilter). In all other ways, this behaves the same as sendBroadcast(Intent).
    - One example of a sticky broadcast sent via the operating system is ACTION_BATTARY_CHANGED. When you call registerReceiver() for that action — even with a null BroadcastReceiver — you get the Intent that was last Broadcast fot that action. Hence, you can use this to find the state of the battery without necessarily registering for all future state change in the battery.

* Describe how broadcasts and intents work to be able to pass messages around your app?

* What is a `PendingIntent`?
    - A PendingIntent is a token that you give to a foreign application (e.g. NotificationManager, AlarmManager, Home Screen AppWidgetManager, or other 3rd party applications), which allows the foreign application to use your application's permissions to execute a predefined piece of code.
    - If you give the foreign application an Intent, it will execute your Intent with its own permissions. But if you give the foreign application a PendingIntent, that application will execute your Intent using your application's permission.

* What are the different types of Broadcasts?
There are two types of broadcasts received by receivers and they are:
    - Normal Broadcasts:
        - These are asynchronous broadcasts.
        - Receivers of this type of broadcasts may run in any order, sometimes altogether.
        - This is efficient.
        - Receivers cannot use the result.
        - They cannot abort the included APIs.
        - These broadcasts are sent with Context.sendBroadcast
    - Ordered Broadcasts
        - These are synchronous broadcasts.
        - One broadcast is delivered to one receiver at a time.
        - Receivers can use the result. In fact as each receiver executes, result is passed to next receiver.
        - Receiver can abort the broadcast and hence no broadcast is received by other receivers.
        - The order of receivers is managed and controlled by the attribute android:priority in corresponding intent-filter.
        - If receivers will have same priority then they may run in any order.

#### Services

* What is `Serivce`? [Developer Android](https://developer.android.com/guide/components/services)
    - A Service is an application component that can perform long-running operations in the background, and it doesn't provide a user interface. Another application component can start a service, and it continues to run in the background even if the user switches to another application. Additionally, a component can bind to a service to interact with it and even perform interprocess communication (IPC). For example, a service can handle network transactions, play music, perform file I/O, or interact with a content provider, all from the background.
    - Foreground
    A foreground service performs some operation that is noticeable to the user. For example, an audio app would use a foreground service to play an audio track. Foreground services must display a Notification. Foreground services continue running even when the user isn't interacting with the app.
    - Background
    A background service performs an operation that isn't directly noticed by the user. For example, if an app used a service to compact its storage, that would usually be a background service.
    - Bound
    A service is bound when an application component binds to it by calling bindService(). A bound service offers a client-server interface that allows components to interact with the service, send requests, receive results, and even do so across processes with interprocess communication (IPC). A bound service runs only as long as another application component is bound to it. Multiple components can bind to the service at once, but when all of them unbind, the service is destroyed.

* `Service` vs `IntentService`. [StackOverflow](https://stackoverflow.com/a/15772151/5153275)
    - When to use?
        - The Service can be used in tasks with no UI, but shouldn't be too long. If you need to perform long tasks, you must use threads within Service.
        - The IntentService can be used in long tasks usually with no communication to Main Thread. If communication is required, can use Main Thread handler or broadcast intents. Another case of use is when callbacks are needed (Intent triggered tasks).

    - How to trigger?
        - The Service is triggered by calling method startService().
        - The IntentService is triggered using an Intent, it spawns a new worker thread and the method onHandleIntent() is called on this thread.
    - Runs On
        - The Service runs in background but it runs on the Main Thread of the application.
        - The IntentService runs on a separate worker thread.

* What is a `JobScheduler`? [Vogella](http://www.vogella.com/tutorials/AndroidTaskScheduling/article.html)
	- This is an API for scheduling various types of jobs against the framework that will be executed in your application's own process.


#### Inter-process Communication

* How can two distinct Android apps interact?  [Developer Android](https://developer.android.com/training/basics/intents)
    - Intents

* Is it possible to run an Android app in multiple processes? How?

* What is AIDL? Enumerate the steps in creating a bounded service through AIDL. [Developer Android](https://developer.android.com/guide/components/aidl)

* What can you use for background processing in Android?  [Developer Android](https://developer.android.com/guide/background)

* What is a `ContentProvider` and what is it typically used for? [Developer Android](https://developer.android.com/guide/topics/providers/content-provider-basics) [Developer Android](https://developer.android.com/guide/topics/providers/content-providers)

#### Long-running Operationsa

* How would you perform a long-running operation in an application?

* Why should you avoid to run non-ui code on the main thread?

* What is ANR? How can the ANR be prevented? [Developer Android](https://developer.android.com/topic/performance/vitals/anr.html)

* What is an `AsyncTask`?  [Developer Android](https://developer.android.com/reference/android/os/AsyncTask)
    - AsyncTask enables proper and easy use of the UI thread. This class allows you to perform background operations and publish results on the UI thread without having to manipulate threads and/or handlers.
    - Should be fast work, tied to Activity to update UI.

* What are the problems in asynctask?

* When would you use java thread instead of an asynctask?
    - Network operations which involve moderate to large amounts of data (either uploading or downloading)
    - High-CPU tasks which need to be run in the background
    - Any task where you want to control the CPU usage relative to the GUI thread

* What is a `Loader`? (Depricated) [Developer Android](https://developer.android.com/guide/components/loaders)

* What is the relationship between the life cycle of an `AsyncTask` and an `Activity`? What problems can this result in? How can these problems be avoided?
    An Asynctask doesn't depend on Activity life-cycle that contains it. Like if we start an AsyncTask inside an Activity and then we rotates the device, the Activity will be destroyed at that point but the AsyncTask will remain same or not die until it completes.
    Then, when the AsyncTask complete its background work its directly updates Activity ui without creating new instance of activity or without affecting activity lifecycle.
    Theres also the potential for this to result in a memory leak since the AsyncTask maintains a reference to the Activty, which prevents the Activity from being garbage collected as long as the AsyncTask remains alive.
For these reasons, using AsyncTasks for long-running background tasks is generally a bad idea . Rather, for long-running background tasks, a different mechanism like service or intent service should be used.

* Explain `Looper`, `Handler` and `HandlerThread`. [MindOrks](https://blog.mindorks.com/android-core-looper-handler-and-handlerthread-bd54d69fe91a) and [MindOrks Video](https://www.youtube.com/watch?v=rfLMwbOKLRk&list=PL6nth5sRD25hVezlyqlBO9dafKMc5fAU2)

#### Working With Multimedia Content

* How do you handle bitmaps in Android as it takes too much memory? [Developer Android](https://developer.android.com/topic/performance/graphics/load-bitmap) [Developer Android](https://developer.android.com/topic/performance/graphics/manage-memory)

* What is the difference between a regular `Bitmap` and a nine-patch image?

* Tell about the `Bitmap` pool. [MindOrks](https://blog.mindorks.com/how-to-use-bitmap-pool-in-android-56c71a55533c)

* How to play sounds in Android? [Vogella](http://www.vogella.com/tutorials/AndroidMedia/article.html)

#### Data Saving

* How to persist data in an Android app? [MindOrks](https://blog.mindorks.com/android-shared-preferences-in-kotlin)

* What is ORM? How does it work?

* How would you preserve `Activity` state during a screen rotation? [StackOverflow](https://stackoverflow.com/questions/3915952/how-to-save-state-during-orientation-change-in-android-if-the-state-is-made-of-m)
    - On newer versions of Android and with the compatibility library, retained fragments are usually the best way to handle keeping expensive-to-recreate data alive across activity destruction/creation. And as Dianne pointed out, retaining nonconfiguration data was for optimizing things like thumbnail generation that are nice to save for performance reasons but not critical to your activity functioning if they need to be redone - it's not a substitute for properly saving and restoring activity state.

* What are different ways to store data in your Android app? [Developer Android](https://developer.android.com/guide/topics/data/data-storage)
Android provides several options for you to save your app data. The solution you choose depends on your specific needs, such as how much space your data requires, what kind of data you need to store, and whether the data should be private to your app or accessible to other apps and the user.
    - Internal file storage: Store app-private files on the device file system.
    - External file storage: Store files on the shared external file system. This is usually for shared user files, such as photos.
    - Shared preferences: Store private primitive data in key-value pairs.
    - Databases: Store structured data in a private database.

#### Look and Feel

* What is a `Spannable`? [Medium](https://medium.com/androiddevelopers/underspanding-spans-1b91008b97e4)

* What is a `SpannableString`?
   - A SpannableString has immutable text, but its span information is mutable. Use a SpannableString when your text doesn't need to be changed but the styling does. Spans are ranges over the text that include styling information like color, highlighting, italics, links, etc

#### Memory Optimizations

* What is the `onTrimMemory()` method?
   - Called when the operating system has determined that it is a good time for a process to trim unneeded memory from its process. This will happen for example when it goes in the background and there is not enough memory to keep as many background processes running as desired

* How does the OutOfMemory happens?
   - Thrown when the Java Virtual Machine cannot allocate an object because it is out of memory, and no more memory could be made available by the garbage collector

* How do you find memory leaks in Android applications? [MindOrks](https://mindorks.com/blog/detecting-and-fixing-memory-leaks-in-android)

#### Battery Life Optimizations

* How to reduce battery usage in an android application? [MindOrks](https://blog.mindorks.com/battery-optimization-for-android-apps-f4ef6170ff70)

* What is Doze? What about App Standby? [Developer Android](https://developer.android.com/training/monitoring-device-state/doze-standby)

* What is `overdraw`? [Developer Android](https://developer.android.com/topic/performance/rendering/overdraw.html)

#### Supporting Different Screen Sizes

* How did you support different types of resolutions?

#### Permissions

* What are the different protection levels in permission?

#### Native Programming

* What is the NDK and why is it useful?

* What is renderscript? [MindOrks](https://blog.mindorks.com/comparing-android-ndk-and-renderscript-1a718c01f6fe)

#### Android System Internal

* What is the Dalvik Virtual Machine?

* What is the difference JVM, DVM and ART?

* What are the differences between Dalvik and ART?

* What is DEX?

* Can you manually call the Garbage collector?

#### Debugging and Programming Tools

* What is ADB?

* What is DDMS and what can you do with it?

* What is the StrictMode? [MindOrks](https://blog.mindorks.com/use-strictmode-to-find-things-you-did-by-accident-in-android-development-4cf0e7c8d997)

* What is Lint? What is it used for?

#### Others

* Why Bundle class is used for data passing and why cannot we use simple Map data structure

* How do you troubleshoot a crashing application?

* Explain Android notification system?

* What is the difference between Serializable and Parcelable? Which is the best approach in Android?

* Have you developed widgets? Describe. [MindOrks](https://blog.mindorks.com/android-widgets-ad3d166458d3)

* What is AAPT?

* What is the best way to update the screen periodically?

* FlatBuffers vs JSON. [MindOrks](https://blog.mindorks.com/why-consider-flatbuffer-over-json-2e4aa8d4ed07)

* `HashMap`, `ArrayMap` and `SparseArray` [MindOrks](https://blog.mindorks.com/android-app-optimization-using-arraymap-and-sparsearray-f2b4e2e3dc47)

* What are Annotations? [MindOrks](https://blog.mindorks.com/creating-custom-annotations-in-android-a855c5b43ed9), [Link](https://blog.mindorks.com/improve-your-android-coding-through-annotations-26b3273c137a), [Video](https://www.youtube.com/watch?v=LEb9if2HHSw)

* How to handle multi-touch in android [GitHub](https://arjun-sna.github.io/android/2016/07/20/multi-touch-android/)

* How to implement XML namespaces?

* What is the support library? Why was it introduced?[MartianCraft](http://martiancraft.com/blog/2015/06/android-support-library/)

* What is Android Data Binding? [Developer Android](https://developer.android.com/topic/libraries/data-binding/index.html)

* What are Android Architecture Components? [MindOrks](https://blog.mindorks.com/what-are-android-architecture-components)

* How to implement search using RxJava operators? [MindOrks](https://blog.mindorks.com/implement-search-using-rxjava-operators-c8882b64fe1d)

