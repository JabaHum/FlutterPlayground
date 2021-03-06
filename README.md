# Flutter Playground
Playing around with flutter. Figuring out if it is for babies or not.

# Apps
1. Quiz app
    - https://github.com/mitchtabian/FlutterPlayground/tree/quiz-app
2. Listview with static data
    - https://github.com/mitchtabian/FlutterPlayground/tree/listview-static-data
3. Expense Tracker
    - https://github.com/mitchtabian/FlutterPlayground/tree/Expense-Tracker
4. Recipes app
    - https://github.com/mitchtabian/FlutterPlayground/tree/Recipes-App


# Resources:
1. Travel Information app:
	- https://www.youtube.com/watch?v=pTJJsmejUOQ
2. Flutter and Dart - The Complete Guide:
	- https://www.udemy.com/course/learn-flutter-dart-to-build-ios-android-apps
3. Widget catalog:
	- https://flutter.dev/docs/development/ui/widgets
4.


# Continue
1. https://www.udemy.com/course/learn-flutter-dart-to-build-ios-android-apps/learn/lecture/14951040#content



# Third Party libs
1. Dates
	- Intl: https://pub.dev/documentation/intl/latest/
2.



# Questions
1. Debugging
2. state
3. architecture?
	- block pattern?
4. Testing?
5. Restoring list position? (after rotation/background or forward/back navigation)
6. Dialog behavior on rotation/background
7. ListView performance
	1. Does is load everything even if not visible?
		- ListView.builder() vs ListView(children: [])
8. Asynchronous work?
	- Is there a "main thread" issue?
9. Memory leaks?
    - Can you leak memory?
    - how can you detect? (ex: Leak Canary on android)



# Things I like
1.




# Day 1 (June 2)
1. Kinda neat. Interesting state management

# Day 2 (June 3)
1. I like how some color opacity's come prebuilt as constants.
	- ex: black12, black26, black87, etc..
	- makes things more consistent across different apps.
	- Gives description. Ex: "This is a good constrasting color for light themes."
2. Images
	- It is way easier to display a simple image. No third party library needed. No async knowledge.
3. Assets
	- Getting stuff from assets is much easier. No need for context or any of that BS. Just write the path and boom you got it.

# Day 3 (June 4)
1. Finished ListView + DetailView with static data example
	- https://github.com/mitchtabian/FlutterPlayground/tree/listview-static-data
	- I'm not amazed by this. I could have built the same thing on android with the same amount of code and time.
	- I guess the fact that it is **cross platform** is the real payoff.
2. Dates
	- https://pub.dev/packages/intl#-readme-tab-
	- Working with dates is very easy with intl third party library.
3. Inputs
	1. All inputs must be Strings?
		- Obviously I don't like this. b/c you have to do the conversions yourself after the fact.
4. SingleChildScrollView
	- Like a ScrollView?
	- This is cool. It would be nice if a Recyclerview was this easy to hook up and delegate scroll behavior to the parent. Often times it has issues if multiple views that can detect gestures are involved. But I wonder... What is the performance like with a massive list? Say 1000 entries with media?

# Day 4 (June 11)
1. ListView
	- ListView.builder(itemBuilder: <>, itemCount: <>) will **not** load items that are not visible
		- This is the `Recyclerview` equivalent
		- itemBuilder: is the RecyclerView Adapter basically
	- ListView(children[]) will load ALL items, even if they are not visible on screen.
2. showModalBottomSheet(context: ctx, builder: (bCtx){})
	- This is a nice built-in widget for displaying a bottom sheet. Pretty convenient.
	- video: `91. Showing a Model Bottom Sheet` @ 7:55
3. Navigator
	1. Navigator.of(context).pop();
		- Navigator is a "global" navigation object? Like the backstack on android?
4. ThemeData(primarySwatch: Colors.purple)
	- This is cool. You can easily set the theme to a variety of pre-packaged material colors.
	- this isn't that much different than what native does though. You have a theme in stlyes.xml
	- *However* this is much less confusing than with android. There is so many different themes and sub-themes. Some don't work with others and cause problems. Flutter seems very straightforward.
	- video: `93: configuring and using themes`
5. Creating a Chart
	1. Creating/drawing shapes is extremely simple compared to native.
		- `100. Creating Bars for our Chart`
6. FittedBox widget
	- automatically shrinks text to fit a box
	- on android this would be difficult to implement. You'd have to calculate the space and manually set the text size based on testing. With Flutter there is a simple widget that does this.
7. showDatePicker(context: null, initialDate: null, firstDate: null, lastDate: null)
    - nice packaged way to show a date picker


# Day 5 (June 12)
1. trailing/leading attributes in a ListTile
    - Ex: (trailing) Trash can icon at the end of a list item layout. Convenient since this is very common
    - Ex: (leading) Something at the front of a list item layout. 
2. Nested Scrolling
    - If you have a SingleChildScrollView and a Listview inside it, it works as you would expect. Which is not the case on android. Scrolling is "difficult" to deal with regarding nesting.
    - But on flutter it is simple. Whichever widget you touch will scroll.
3. MediaQuery
    - This isn't better than what we have available on android. I prefer the layout designs using xml for this.
    1. holds information:
        - Screen pixel ratio
        - disable animations
        - brightness
        - size (width and height of device)
4. LayoutBuilder
    - can wrap a widget in this to apply constraints or get information about the sizing. Similar to ViewTreeObserver on android.
        - `119. Using the LayoutBuilder widget`
5. SystemChrome
    - Set allowed device orientations (force portrait only or landscape only)
    - system wide settings for application
    - `WidgetsFlutterBinding.ensureInitialized();` 
    - `SystemChrome.setPreferredOrientations(
             [DeviceOrientation.portraitUp, DeviceOrientation.portraitDown]
         );`
6. Build and Flutter Widget Tree
    - `137: Widget Tree & Element Tree`
7. Lifecycle states
    - `WidgetsBindingObserver`
    - How to listen for the various lifecycle states in a particular widget or app: `146. Understanding the App Lifecycle`

# Day 6 (June 16)
1. End Expense Tracker app. Beginning to work on Navigation. 
    - (`https://www.udemy.com/course/learn-flutter-dart-to-build-ios-android-apps/learn/lecture/15033798#overview`)
2. InkWell
    - Same as GestureDetector but fires off a ripple effect when tap occurs
3. Navigator
    - `159. Navigating to a New Page`
    - `160. Passing Data via the Constructor`
    - MaterialPageRoute
    - Navigation is much simpler. Especially regarding passing arguments to a new screen.
        1. You can pass constructor arguments to the widgets. On Android you have to use bundles. Much more complex.
          - Fragments/Activities can accept constructor arguments, but you must use a Factory (complex).
        2. You can easily access the application stack and push/pull whatever you want with Navigator.
    - **downside**
        - This is simple, but I could see this getting cumbersom in a large app. Named Routes seem like a better approach. In which case it is not really simpler. It's basically the same as NavigationComponents.
4. Named Routes
    - `161. Named Routes and Passing Data with Named Routes`
    - Very similar to website navigation.
    - This is a better option for a larger app. Basically you define all the navigation in a "map".
    - Advantages: 
        1. All routes are defined in main widget so if any application-wide state variables need to be managed it's easy to pass to constructor.
5. Rounded images
    - `165. Displaying Recipe Items & Using Network Images`
    - Widget: `ClipRRect`
        - Clip the corners of an image
6. Network images
    - `165. Displaying Recipe Items & Using Network Images`
    - `Image.network(src)`
    - Very easy to display a network image. With Android this is very confusing for beginners because third party libraries are technically the best way. And there is so many.
    - No worries about asynchronous loading?... 
    - No worries about blocking the ui thread?...

# Day 7 (June 17)
1. onUnknownRoute
    - Basically this is the web equivalent of a 404 page. 
    - MaterialApp param
2. onGenerateRoute
    - dynamically generate a route (could be used for dynamically generating screens)
    - MaterialApp param
3. Top Tabs
    - `170. Adding TabBar to the AppBar`
    - https://gist.github.com/mitchtabian/d16b239d849f8d175d1f6801011dc0ef
    - DefaultTabController
    - This was very easy to set up and looks good. Much easier than setting this up natively. Very intuitive.
4. Bottom Tabs
    - `171. Adding a bottom TabBar`
    - https://gist.github.com/mitchtabian/01c54ffb9362b592641349d7e0d7467b
    - Interestingly, setting tabs up on the bottom is much more difficult than tabs on the top. This is not intuitive.
5. Navigation drawer
    - `172. Adding a custom drawer`
    - Drawer param in a scaffold
    - Pretty simple. But I wouldn't say this is necessarily simpler than on native.
6. removing items from backstack when navigating
    - `Navigator.of(context).pushReplacementNamed(NAV_TABS_SCREEN)`
    - This replaces the existing page on the backstack when navigating. This is equally simple on native (with Nav components).
7. State management
    - I have a lot of questions about state management at this point. Because in the course if we want to manage some kind of "global" property we have to pass it around widget constructors which gets very complicated. I believe later in the course I will learn a better system.



# Thoughts on Flutter
1. June 11
	- I think Flutter became very popular among "new" developers because:
		1. cross platform
		2. it's easier to hack something together that works. There aren't as many architectural patterns, architectures, etc... And much less judgement from the developer community. Like if you build a piece of shit on native and show the community, they will crucify you. But if you did the same thing with flutter, I doubt anyone would say much. 
2. June 12
    - Nothing to say today. 
3. June 16
    1. Navigation
        - Navigation is much simpler. Especially regarding passing arguments to a new screen.
        - 2 things make it simpler:
            1. You can pass constructor arguments to the widgets. On Android you have to use bundles. Much more complex.
                - Fragments/Activities can accept constructor arguments, but you must use a Factory (complex).
            2. You can easily access the application stack and push/pull whatever you want with Navigator.
4. June 17
    1. I love the way you can build layouts in flutter.
        - I wish I could design layouts natively like Flutter does. Hopefully compose allows this.
    2. Setting up tabs was pretty easy. Definitely much more beginner friendly than with native.
    3. Performance wise, it seems like the biggest thing you need to watch out for is prevent widget rebuilds whenever possible. So proper state management is key.
5. 































