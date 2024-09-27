---
layout: post
section-type: post
has-comments: true
title: "Broadcast"
category: android
---

<aside>
💡 The system-wide events occurred on the device. We can register for the broadcast receiver and application events, and when that event happens, the receiver gets notified.

</aside>

### Create Broadcast Receiver

In the activity you want to receive unread messages from the chat:

```kotlin
private val mMessageReceiver: BroadcastReceiver = object : BroadcastReceiver() {
		// update unread message numbers
    override fun onReceive(context: Context?, intent: Intent) {
        val unreadMessage = intent.getIntExtra("message", 0)
    }
}
```

### Register the Broadcast Receiver

In the activity’s `onCreate()` method:

```kotlin
LocalBroadcastManager.getInstance(requireContext()).registerReceiver(
    mMessageReceiver,
    IntentFilter("chat-message")) 
		// Custom action name, the event will notify the receiver
```

### Send Broadcast

In the activity you can get chat messages:

```kotlin
// Event happens
val intent = Intent("chat-message")
intent.putExtra("message", 1)
LocalBroadcastManager.getInstance(this).sendBroadcast(intent)
```