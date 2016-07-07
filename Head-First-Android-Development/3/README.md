# Chapter 3: Multiple Activities and Intents: State your Intent

## Apps can contain more than one activity
- We need an app that has multiple layouts so we can simulate having multiple views
- Here's what we're going to do
  - (1) Create a basic app with a single activity and layout
  - (2) Add a second activity and layout
  - (3) Get the first activity to call the second activity
  - (4) Get the first activity to pass data to the second activity

## Here's the app structure
- (1) When the app gets launched, it starts activity CreateMessageActivity
- (2) The user clicks on a button in CreateMessageActivity
  - Launches a different activity
- We created a new project

## Update the layout
- Add code from book to activity.xml file
- Have new <EditTexT> element, which is a text field with editable text
  - ems layout property is how many characters wide it should fit

## Update strings.xml and the method to the activity
- Need to add localized strings
- Need to add onClickMethod

## Create the second activity and layout
- Android Studio has wizard for new activities and layouts similar
to the wizard to create a project but cut down
- File->New->Activity

## What just happened?
- Made a layout and activity parallel to the ones from the project wizard
- Also made an AndroidManifest.xml that's used to change the app

## Welcome to the Android manifest file
- Has information about the layouts, where to start with them when it launches
- Activities need to be declared in AndroidManifest.xml for the system to know they
exist

## An intent is a type of message
- We need to try to get CreateMessageActivity to call ReceiveMessageActivity when
the user clicks the button
- When you want an activity to start a second activity you use an intent
  - "An intent to do something"
- Intent intent = new Intent(this, Target.class);
- startActivity(intent)
- throws ActivityNotFoundException if it is loaded and found

## Use an intent to start the second activity
- Add code to onSendMessage method

## Test drive the app
- Clicking on the button displays the new activity
- No text or passing of data

## Pass text to a second activity
- We need to setup input and outputs for the current activities

## putExtra() puts extra information in an intent
- intent.putExtra(STRING_KEY, value);
- getIntent() returns the intent that started the activity
- String string = intent.getStringExtra("message");
- Can also do non-string values
  - int intNum = intent.getIntExtra("name", default_value);
  - default_value defines a value if there is not one set as an extra

## Update the CreateMessageActivity code
- Use the above code in the onSendMessage() method

## Get ReceiveMessageActivity to use the information in the intent
- Add to the onCreate method in ReceiveMessageActivity

## We can change the app to send messages to other people
- We can use activities of other apps in our app to communicate with other
services

## How Android apps work
- A collection of activities/layout
- We can use intents to start activities in other apps
- Use an intent to start an email in Gmail

## But we don't know what apps are on the device
- Three questions need to be answered before we can call other app's activities
  - How do we know activities are available on the user's device?
  - How do we know which of these activities are appropriate for what we
  want to do?
  - How do we know how to use these activities?
- We're going to use actions
  - Actions are a way of telling Android what standard operations an activity
  can perform

### Here's what you're going to do
- Create an intent that specifies an action
- Allow the user to choose which app to use

## Create an intent that specifies an action
- Using new Intent(this, MyClass.class) is an explicit intent
  - If you don't care which activity opens you can use an implicit intent
- new Intent(action)
  - Intent.ACTION_DIAL
  - Intent.ACTION_WEB_SEARCH
  - Intent.ACTION_SEND
- Add extra information to pass our data to the activity
  - intent.setType("text/plain")
  - intent.putExtra(Intent.EXTRA_TEXT, messageText);
  - intent.putExtra(Intent.EXTRA_SUBJECT, subject);

## Change the intent to use an action
- Instead of an explicit intent let's use an implicit intent in
CreateMessageActivity

## What happens when the code runs
- (1) When onSendMessate() is called an intent gets created and startActivity()
passes the intent to Android
- (2) Android sees that intent can only be passed to activities able to handle
ACTION_SEND and text/plain data
- (3) If only one activity is able to receive the intent, Android starts the activity
and passes it the intent
- (4)If more than one activity is able to receive the intent, Android displays
a dialog to choose which one the user wants
- (5) When the user chooses the activity, Android goes to the activity
and passes it the intent

## The intent filter tells Android which activities can handle which actions
- Intent resolution: figuring out which activities can handle an implicit intent
- <intent-filter> in AndroidManifest.xml allows us to register for an intent

## How Android uses the intent filter
- Android only uses activities who's intent-filter matches the intent per
properties and type

## You need to run your app on a REAL device
- We need to run on a real device so there's more than one app per intent
- (1) Enable USB debugging on your device
- (2) Set up your system to detect your device (driver)
- (3) Plug your device into your computer with a USB cable

## Test drive the app
- The button now opens it in an activity

## What if you ALWAYS want your users to choose an activity?
- There's a way using choosers to guarentee a user can choose an activity
every time they click on the Send Message button
- Intent.createChooser() displays a chooser dialog
  - Intent chosenIntent = Intent.createChooser(intent, "Send message...")
  - Returns a new explicit intent
  - use startActivity(chosenIntent) to start the intent they picked

## What happens when you call createChooser()
- (1) the createChooser() method gets called
- (2) Android checks which activities are able to receive the intent by
looking at their intent filters: actions, type of data, categories
- (3) If there's more than one activity available Android asks the user
what they want to use
- (4) The user chooses an activity and Android creates a new explicit intent
describing the activity
- (5) The activity asks Android to start the activity specified in the intent
- (6) Android asks the activity specified by the intent to start and then
passes it the intent

## Change the code to create a chooser
- We're going to update our code to include a chooser

## Test drive your app
- If you have one activity it'll look the same
- More than one activity will have clear difference
- If there are no activities, your message will be clearly displayed

## Your Android Toolbox
- A task is two or more activities chained together
- The <EditText> element defines a text field that is editable. It inherits
from the Android View class
- You acn add a new activity in Android Studio by choosing File->New->Activity
- Each activity you create must have an entry in AndroidManifest.xml
- An intent is a type of message that Android components use to communicate
with one another.
- An explicit intent explicitly specifies the component the intent is targeted
at. You create an explicit intent using Intent intent = new Intent(this, Target.class);
- To start an activity, call startActivity(intent). If no activities are found, it
throws an ActivityNotFoundException
- Use putExtra() method to add extra information to an intent
- Use getIntent() method to retrieve the intent that started the activity
- use the get*Extra() method to retrieve extra information associated with the intent.
getStringExtra() retrieves a String, getIntExtra() retrieves and int, etc.
- An activity action describes a standard operational action an activity
can perform. To send a message, use Intent.ACTION_SEND
- To create an implicit intent that specifies an action use
Intent intent = new Intent(action);
- To describe the type of data in the intent, use the setType() method
- Android resolves intents based on the named component, action, type of data,
and categories specified in the intent. It compares the contents of the
intent with the intent filters in each app's AndroidManifest.xml. An
activity must have a category of DEFAULT if it is to receive an implicit intent
- The createChooser() method allows you to override the default Android activity
chooser dialog. It allows you to specify a title for the dialog, and doesn't
give the user the option of setting a default activity. If no activities can
receive the intent it is passed, it displays a message. The createChooser()
method returns an Intent.
- You retrieve the value of a string resource using getString(R.string.stringname);

[END CHAPTER]