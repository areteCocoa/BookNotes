# Chapter 4: The Activity Lifestyle: Being an Activity
- Lets take a closer look at activities

## How do activities really work?
- An app is a collection of activities, layouts and other resources
- By default each app runs within its own process
- You can start an activity in another application by passing an intent
with startActivity()
- When an activity needs to start, Android checks if there's already a
process for that app
- When Android starts an activity, it calls its onCreate() method
- There are things we still don't know
  - How long do activities live?
  - What happens when it disappears from screen?
  - What happens if its interupted by a phone call?
- We want the control over our activities

## The Stopwatch app
- We're going to explore the lifecycle with a stopwatch app
- App can start, stop or reset a stopwatch (counter)
### Build the app
- Give me just enough code to start but not everything

## How the activity code will work
- Each button has its own onClick method which we'll use to control
the stopwatch
- Have some private fields to store the state of the stopwatch

## The runTimer() method
- We have a private method that updates the TextView
- The code needs to loop in a way that doesn't block main thread
- Can't use background thread because they can't update the interface
(an exception is thrown)
- Use `Handler`

## Handlers allow you to schedule code
- Schedule code to be run some time in the future
- Post code to run on a different thread
- Wrap code in a `Runnable` object and use `Handler.post()` or
`Handler.postDelayed()`

### The post() method
- Post code that needs to be run ASAP
- Takes one parameter that is object `Runnable`

### The postDelayed() method
- Post code that needs to be run after a delay
- Takes a Runnable and a long
  - Runnable is the object that contains the code you want to run
  - long is number of milliseconds to delay code by
  
## The full runTimer() code
- We're going to repeatedly schedule code with Handler with a 1k millisecond
delay

## What happens when you run the app
- (1) The user decides they want to run the app
- (2) The AndroidManifest.xml file for the app specifies which activity
to use as the launch activity
- (3) Android checks if there's already a process running for the app,
and if not, creates a new process
- (4) The onCreate() method in the activity gets called
- (5) When the onCreate() method, finishes, the layout gets displayed
on the device

## Test drive the app
- We can start, stop and reset everything
- The app works great! Until the device is rotated and it stops running
and is set to 0

## What just happened?
- The user starts the app and clicks on the start button to set the stopwatch
going
- The user rotates the device
  - Android sees that the device constraints have changed and destroys the
  activity and it's variables
- `StopwatchActivity` is re-created

## Rotating the screen changes the device configuration
- Configuration includes screen size, orientation and keyboard attached
  - User defined: locale
- Configuration changes how the app runs
  - French locale changes localization
  
## From birth to death: the states of an activity
- Activity is launched but not running yet - *launched*
- The main state is *running* or *active*
  - The activity is in the foreground and the user can interact with it
- At the end of its life it moves to being *destroyed*
- Key methods are `onCreate()` and `onDestroy()`
  - `onCreate()` is all the setup and should always been overriden
  - `onDestroy()` is the final code to run before an object is destroyed
  
## The activity lifecycle: from create to destroy
1. The activity gets launched
   - Created with constructor
2. The onCreate() method runs immediately after the activity is launched
3. An activity is running when it's visible in the foreground and the user
can interact with it
4. The onDestroy() method runs immediately before the activity is destroyed
5. After the onDestroy() method runs, the activity is destroyed

## Your activity inherits the lifecycle methods
- Activities extend android.app.Activity, inherit a bunch of lifecycle
methods
	- Extend more than just Activity because Activity is a subclass of
	a class chain
- `android.content.Context` is an interface to global information about
the app environment. Allows access to app resources, classes and app-level
operations
	- Abstract class
- `android.content.ContextWrapper` is a proxy implementation for the Context
- `android.view.ContextThemeWrapper` allows modifications of the ContextWrapper
- `android.app.Activity` implements default versions of lifecycle methods
and defines methods like findViewById(Int) and setContentView(view)
- `Your activity class` overrides default methods to make your app do things

## How do we deal with configuration changes?
- There's two ways to deal with configuration changes
  - Tell android to bypass restarting the activity
  - Save the current state so the activity can recreate itself in the same state
  
### Bypass re-creating the activity
- Usually not the best option but is an option
- Add to AndroidManifest.xml
  - `android:configChanges="configuration_change"`
  - `configuration_change` is the type of config change
  - We would use `orientation|screenSize`
- Calls `onConfigurationChanged(Configuration) in activity instead of
recreating it

### Or save the current state...
- Save the current state of the object and then reinstate it in the new
`onCreate()` call
- Implement `onSaveInstanceState()` - gets called before the activity
gets destroyed and save any values
- Takes one parameter, a `Bundle`
  - Allows you to gather many different datas of different types together
- `onCreate()` is passed this `Bundle` as a parameter
- `bundle.put*("key", value)`

### ...then restore the state in onCreate()
- `Bundle` is going to be passed to onCreate method
- `bundle.get*("key");`

## What happens when you run the app
1. The user starts the app, and clicks on the start button to set the stopwatch
going
2. The user rotates the device
3. All the activity data gets saved into a `Bundle`
4. Android destorys the activity and then re-creates it
5. The `Bundle` contains the values of the seconds and running variables as they
were before the activity was destroyed
6. The `runTimer()` method gets called and the timer picks up where it
left off

## Test drive the app
- It works even when we rotate it!

## There's more to an activity's life than create and destroy
- What if we get a phone call in the middle of using the app?

### Start, stop and restart
- Theres additional methods to `onCreate()` and `onDestroy()`
  - `onStart()`
	- Device becomes visible to the user
  - `onStop()`
	- Activity no longer visible to user
	- Could be its hidden or is going to be destroyed soon
  - `onRestart()`
	- After activity has been invisible but is going to be visible again
	
## The activity lifecycle: the visible lifetime
1. The activity gets launched, and the `onCreate()` method runs
2. The `onStart()` method runs after `onCreate()`. It gets called when the activity
is about to become visible
3. The `onStop()` method runs when the activity stops being visible to
the user
4. If the activity becomes visible to the user again, the `onRestart()` method
gets called followed by `onStart()`
5. Finally, the activity is destroyed
   - `onStop()` usually gets called before `onDestroy()` but this can be bypassed
   if there are memory issues
   
## We need to implement two more lifecycle methods
- We need to stop the stopwatch from running when we leave visibility and start
running when we enter visibility

### Implement onStop() to stop the timer
- When you override an Android lifecycle method you must first call super
  - Android generates an exception if you don't

## What happens when you run the app
1. The user starts the app and clicks the Start button to set the stopwatch going
2. The user navigates to the device home screen so the Stopwatch app is no
long visible
3. The user navigates back to the Stopwatch app
   - `onStart()` is called and we resume
   
## Test drive the app
- Everything works

## But what if an app is only partially visible
- You don't have full screen and/or aren't focused
- Two methods to help with this
  - `onPause()` for when you leave focus but are you still visible
  - `onResume()` for when you reenter focus after being paused
  
## The activity lifecycle: the foreground lifetime
1. The activty gets launched and the onCreate() and onStart() methods run
2. The onResume() method runs after the onStart() method. It gets called when
the activity is about to move into the foreground
3. The onPause() method runs when the activity stops being in the foreground
4. If the activity moves into the foreground again, the onResume() method
gets called.
5. If the activity stops being visible to the user, the onStop() method gets called
6. If the activity becomes visible to the user again, the onRestart() method gets
called, followed by onStart() and onResume()
7. Finally, the activity is destroyed
   - onPause() gets called at sometime, as well as onStop()
   
## What happens if the device rotates while the activity is paused?
1. The user launches the activity
   - `onCreate()`, `onStart()` and `onResume()` are all called
2. Another activity appears in front of it
   - `onPause()` is called
3. The user rotates the device
   - `onStop()` and `onDestroy()` are called
4. The activity is visible but not in the foreground
   - `onCreate()` and `onStart()` are called
   - Because it doesn't have focus, `onResume()` is **not** called
   
## Activities can go straight from onStart() to onStop() and bypass onPause() and onResume()
- If you have an activity that is visible but never in the foreground and
never has focus, `onPause()` and `onResume()` never get called

## Stop the stopwatch if the activity's paused
- We can implement `onPause()` and `onResume()`
  - We can ever replace our old `onStop()` and `onStart()` code
  
## What happens when you run the app
1. The user starts the app and clicks on the start button to get the stopwatch going
2. Another activity appears in the foreground, leaving StopwatchActivity partially visible
3. When StopwatchActivity returns to the foreground, the `onResume()` method gets called,
running is set to true, and the number of seconds starts incrementing again

## Test drive the app
- Run the app and notice that when we go out of focus it pauses

## Your Android Toolbox
- Each app runs in its own process by default
- Only the main thread can update the user interface
- Use a `Handler` to schedule code, or post code to a different thread
- A device configuration change results in the activity being destroyed and re-created
- Your activity inherits the lifecycle methods from the Android `Activity` class. If
you override any of these methods, you need to call up the method in the superclass.
- `onSaveInstanceState(Bundle)` enables your activity to save its state before the activity
gets destroyed. You can use `Bundle` to restore state in `onCreate()`
- You add values to a Bundle using `bundle.put*("key", value)` and retrieve values
using `bundle.get*("key")`
- `onCreate()` and `onDestroy()` deal with the birth and death of the activity
- `onRestart()`, `onStart()` and `onStop()` deal with the visibility of the activity
- `onResume()` and `onPause()` deal with when the activity gains and loses focus

[END CHAPTER]
