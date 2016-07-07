# Chapter 2: Building Interactive Apps: Apps That Do Something
- Get activity and layout to interact with each other
- Learn more about Android through "R" -- "the hidden gem that glues
everything together

## You're going to build a Beer Adviser app
- Going to build an app that they interact with
- Type in type of beer they enjoy and we return some tasty beers

## Here's what you need to do
- Here's the overview of what we're going to do
- (1) Create a project
- (2) Update the layout
  - Amend the layout so it has everything we need
- (3) Wire the layout to the activity
  - Make the layout interact with the code
- (4) Write the application logic

## Create the project
- Create in Android Studio
- We used an empty layout again

## We've created a default activity and layout
- Remember that the layout is just an xml file

## Adding components with the design editor
- We're adding components with the design editor
- Added a button

## activity_find_beer.xml has a new button
- Some xml code was added to the xml file
- Look at some of the properties that are very similar to text view's
- That's because both of these are subclasses of Android's view

## A closer look at the layout code
- We're using a relative layout
- Relative Layout: components will be positioned relative to each other
- layout_below and layout_alignLeft are assigned to the button with
the textview as the relative

## Changes to the XML...
- Changes to XML also affects the layout representation
- We're gonna change the XML to layout our components now

## ... are reflected in the design editor
- Look how things in the design editor changed

## Use string resources rather than hardcoding the text
- We'll used localized strings because its a good habit to get into
- Add some code to the strings.xml file

## Change the layout to use the string resources
- Lets change the component's hardcoded strings to use the localized strings

## Let's take the app for a test drive
- Save changes and run the app
- So far we've
  - (1) Created a layout that specifies what the app will look like
  - (2) The file strings.xml includes the string resources we need
  - (3) The activity specifies how the app should interact with the user (but we have no code!)

## Add values to the spinner
- We just need to have an array of string values and have the spinner reference it
- Use <string-array name... > for an array of strings
  - <item> as children tags

## Get the spinner to reference a string-array
- Use "@array/array_name" to reference an array
- Add the array code the layout

## Test drive the spinner
- Save and run the app

## We need to make the button do something
- We need it to do something to retrieve values based on value of spinner
- Lets start by getting the button to call a method

## Make the button call a method
- We need to specify the method to be called in activity_find_beer.xml
- We need to write the method in FindBeerActivity

## Use onClick to say which method the button calls
- android:onClick in layout xml and value is name of method

## What activity code looks like
- extends the Activity class
- overrides onCreate method
  - Set the content view (layout)

## Add an onClickFindBeer() method to the activity
- Receiving method of onClick must accept a view as a parameter
- Need to imprt View class

## onClickFindBeer() needs to do something
- Use findViewById() to reference views in the layout by their id
- R is a special Java class that enables you to retrieve references to resources
in your app
- R.java is generated for you by the compiler

## Once you have a View, you can access its methods

## Update the activity code
- Use a cast and findViewById(R.id.[YOUR_ID])
- TextView.setText

## What the code does
- The code specifies what method should be called and it is called
- We get references to spinner and textview
- Convert the value of the spinner to string
- Set text value of textview to selected item

## Buidling the custom Java class
- package name com.hfad.beeradviser
- BeerExpert class
- Expose one method, getBrands(), that takes a beer color string and returns a list
of strings

## Enhance the activity to call the custom Java class
- Call the BeerExpert class and format it

## Your Android Toolbox
- The Button element is used to add a button
- The Spinner element is used to add a spinner. A spinner is a drop-down list of values
- All GUI components are types of view. They inherit from the Android View class
- Add an array of string values using <string-array> <item></item> </string-array>
- Make a button call a method with android:onClick="clickMethod"
  - Also have the method public void clickMethod(View view)
- R.java is generated for you and is a way to get references to resources in your Java code
- Use findViewByID() to get a reference to a view
- Use setText() to set the text in a view
- Use getSelectedItem() to get the selected item in a spinner
- Add a custom class to an Android project by going to File menu->new->Java class

[END CHAPTER]
