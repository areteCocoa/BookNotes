# Chapter 1. Getting Started: Diving In

## Welcome to Androidville
- Typical Android app consists of Java and XML
- Screens are defined using layouts (usually in XML) and contain several GUI components
- Java code defines what the app should do
  - Activity class decides which layout to use and how to respond to the user
  - Example: If layout has a button, you need java code in the activity to
  define what should happen if the button is pressed
- Need assets as well

## The Android platform dissected
- Platform made of number of different components
  - Core applications such as 'Contacts' a set of APIs to control what
  the app looks like, how it behaves and many other supporting files/libs
- [Diagram for the platform stack]

## Here's what we're going to do
- Lets create a basic Android app
1. Set up a development environment
   - Install Android Studio
2. Build a basic app
   - Use Android Studio to display sample text on a screen
3. Run the app in the Android emulator
4. Change the app
   - Make tweaks to the app and run it again

## Your development environment
- Android doesn't run .class or .jar files, they compile to their own
optimized formats for compiled code, must use a new IDE/SDK - Android SDK

## Install Java
- Download Android Studio and install
- Installing Android Studio is a pain in the ass

## Build a basic app
- Setup, now lets make an app

## Let's build the basic app
1. Create a new project
2. Configure the project
3. Specify the API level
   - API level is used to designate how far back you want to support in terms
   of devices
   - We're choosing API level 15

## Activities and layouts from 50,000 feet
- Next we have to add an activity to the project
- Activity: a single, defined thing that the user can do, usually associated
with one screen
- Layout: the appearance of the screen (written as XML files)
- How they work together:
  1. Device launches your app and creates and activity object
  2. The activity object specifies a lyout
  3. The activity tells Android to display the layout of screen
  4. The user interacts with the layout displayed on the screen
  5. The activity responds to interactions by running app code
  6. Activity updates the display
  7. User sees these updates on the device

## Building a basic app (continued)
4. Create an activity
   - Next screen gives a series of templates for activities and layouts
   - We're making basic activity/layout so choose 'Empty Activity'
5. Configure the activity
   - Need to entire name of screen's activity and layout as well as title
   of screen and menu resource name

## You've just created your first Android app
- Android Studio wizard created the project configured to my specifications
  - It created a basic activity and basic layout with some template code

## Android Studio creates a complete folder structure for you
- Android app is really just a bunch of valid files in a particular folder
structure
- Folder structure includes different types of files
  - Java and XML source files: activity and layout files created by wizard
  - Android-generated Java files: files you don't need to touch that Android
  Studio generates
  - Resource files: Default image files for icons, styles and any common
  strong values your app might want to look up
  - Android libraries: libraries relevant to the selected minimum SDK version
  - Configuration files: tells Android what's in the app and how it should run

## Useful files in your project
- Gradle build system used to compile and deploy apps
- Here are some key files you'll be dealing with [Diagram]

## Edit code with the Android Studio editors
- Code editor opened for code
- Design editor opened for layout files (instead of editing XML)

## Run the app in the Android emulator
- Want to run the app but don't have a device?
- Android emulator lets you run on an 'Android virtual device' (AVD)
- Built on QEMU
- Lets setup an AVD

## Creating an Android Virtual Device
- Open the Android Virtual Device Manager
  - Tools -> Android -> AVD Manager
- Select the hardware
  - Can emulate several types of devices
  - Nexus 4
- Select a system image
  - Can select version of Android on AVD and type of CPU (ARM or x86)
  - Using Lollipop 21 armeabi-v7a Android Open Source Project version
- Verify the AVD configuration
  - You are given chance to verify, then it is created.

## Run the app in the emulator
- Now that you've setup the emualtor, choose "Run 'app'" from the Run menu
- Given choice to choose emulator
- Compile, package, deploy and run
  - Choosing run doesn't just run the app, it deals with preliminary tasks
  needed to run the app
  - (1) Hava source files get compiled to bytecode
  - (2) An Android application package (APK) gets created
  - (3) Assuming there's not one already running, the emulator gets launched
  with the AVD.
  - (4) Once the emulator has been launched at the AVD is active, the APK file
  is uploaded to the AVD and installed
  - (5) The AVD starts the main activity associated with the app
    - All ready to be tested out!

## You can watch progress in the console
- Console will let you know about the whole build process, including any
gradle warning and errors

## Test drive
- First the AVD fires up, then displayed as a locked Android Device
- Unlocked, displays your app!

## What just happened?
- (1) Android Studio launches the emulator, loads the AVD and installs the APK
- (2) When the app is launched, the activity object is created from
MainActivity.java
- (3) The activity specifies that is uses layout activity_main.xml
- (4) The activtiy tells Android to display the layout on the screen
  - Hello World is displayed.
- There are no dumb questions
  - This does not run as Java bytecode in a JVM
  - The .class files are converted to DEX format which is run natively

## Refining the app
- We want to change the app, but first lets look at how it's currently built
  - The app has one activity and one layout
    - Created by the wizard
  - The activity controls what the app does
    - MainActivity.java specifies what the app does and how it should respond
    to the user
  - The layout controls the app appearance
    - MainActivity.java specifies that it uses activity_main.xml, what the
    activity 'looks like'
    - This means to change the appearance of the app we should look at the
    activity_main.xml file

## What's in the layout?
- Open activity_main.xml
- The design editor
  - There's two ways of viewing and editing layout files in AS: Design editor
  and the code editor
- The code editor
  - Content of .xml file is displayed instead
- Can switch between the two at the bottom of the editor of layout.xml files
where it says 'design' and 'text'

## activity_main.xml has two elements
- First is '<RelativeLayout>' element. Tells android to display items in a
relative position
- Second is '<TextView>' element
  - Used to display text to the user
  - Nested within '<RelativeLayout>'
  - Used to display "Hello world!"
  - Key part is 'android:text="@string/hello_world"'

## The layout file contains a reference to a string, not the string itself
- Key part of the '<TextView>' element is first line
  - 'android:text="@string/hello_world" \>
  - android:text means the text property of '<TextView>' so it specifies the
  text of this element
  - Why "@string/hello world" rather than "Hello world!"?
- Android studio created string resource file called strings.xml
  - 'app/src/main/res/values' folder
  - Put in this instead of hardcoding
- '@string' tells Android to look for value in a string resource file
  (strings.xml)
- 'hello_world' means use the associated text value with 'hello_world'
- Do this because of localization

## Let's look in the strings.xml file
- AS created strings.xml for us, let's see if it contains a hello_world resource
- In the file (app/src/main/res/values/strings.xml) there is a line
  - <string name="hello_world">Hello world!</string>
- Update strings.xml to change the text
  - Change the value between the tags to change the text, save and run
- String resource files up close
  - '<resources' element identifies the contents of the file as resources
  - '<string> element identifies the key/value pair as strings
  - Two things that allow Android to recognize strings.xml as string res file
    - The file is held in 'app/src/main/res/values'
    - The file has a '<resources>' element which contains one (or more)
    '<string>' elements
  - Each k/v pair takes the form
    - <string name="string_key">string_value</string>
  - Layouts can access the values of the string using
    - "@string/string_key" (returns the string_value)

## Take the app for a test drive
- Run the app after saving, see how it has the new text (sup doge) now?
- There are no dumb questions
  - This method is not necessary but more helpful
  - Store the string files in files with language specifiers to let the app know
  to use different sets of strings
  - Android studio might have slightly different generated code from the book
  examples. Don't be worried, you'll be learning how to write your own code

## Your Android Toolbox
- Basic android concepts are now in your toolbox!
- Bullet Points
  - Versions of Android have a version number, API level and code name
  - Android Studio is a special version of IntelliJ IDEA that interfaces with
  the Android SDK and the gradle build system
  - A typical Android app is comprised of activities, layouts and resources
  files
  - A layout describes what the app looks like. They're located in
  'app/src/main/res/layout'
  - Activities describes what the app does and how it interacts with the user.
  They're located in 'app/src/main/java'
  - 'strings.xml' contain key/value pairs for localizations
  - 'AndroidMainfest.xml' contains information about the app itself
    - Lives in 'app/src/main'
  - An AVD in an Android Virtual Device. Runs the Android emulator and mimics
  a physical Android device
  - An APK is an Android application package. It's like a JAR file for Android
  apps and contains app bytecode, libraries and resources. Used to install apps
  - Android apps run in separate processes using the Android runtine (ART)
  - 'RelativeLayout' is used to place GUI components in relative positions
  in a layout
  - 'TextView' element is used for displaying text

[END CHAPTER]