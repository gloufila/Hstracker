# Frameworks

HearthstoneTracker is build on the .NET framework and makes heavy use of 3rd party libraries. The main reason for this is that you want to focus on the core functionality of the tool. Writing infrastructure code is boring and there are good open-source libraries and free examples available, providing a lot of this 'boilerplate' code.

This is a list of the libraries you will most commonly encounter:

 * [Caliburn.Micro](https://github.com/Caliburn-Micro/Caliburn.Micro), Provides a full framework for building MVVM style XAML applications (in our case: WPF). You will see caliburn mostly in user interface code (xaml/viewmodels).
 * [EntityFramework](http://www.asp.net/entity-framework), Used as an object-relational mapper for our data model (stored in SQL Compact 4). Also used for database migrations (upgrades) between versions.
 * [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/en-us/library/dd460648(v=vs.110).aspx), Used for service location and dependency injection. Most components (like viewmodels / services / repositories) are registered using MEF, allowing easy wiring and resolving of those components.
 * [MahApps.Metro](http://mahapps.com), Windows 8 user interface elements and styles. 

Other 3rd party libraries include NLog (for logging), MetroChart, OxyPlot, EasyHook (for direct3d hook) and some others you most likely wont have to worry about.

# Architecture

## HearthCap (Main application)

The project is split up in several parts, explained below.

 * Infrastructure
 * Shell
 * Features
 * Framework

### Shell

This is the main application 'shell'. It should have almost no application specific functionality. The shell can be seen as the main template where you can put in your custom components, like tabs, menu's, fly-outs, etc.

The shell provides interfaces like ITab, IFlyout and IWindowCommand that allow you to create (and add) new UI elements into the shell. If you register them in MEF using those interfaces, they get added to the application automatically.

For example:
```C#
[Export(typeof(IFlyout))]
public class DeckSettingsViewModel : FlyoutViewModel,
...
[Export(typeof(IWindowCommand))]
public class AboutCommandBarViewModel : WindowCommandViewModel
```

The shell also provides some services like in app notifications (SendNotification event), registry settings, themes and working with the tray icon.

### Features

This is where the real functionality is implemented. In a lot of (smaller) projects using the MVVM pattern, you see the use of a 'Views' and 'ViewModels' folder. Splitting up the xaml and the code to different folders. Personally having used this style in smaller and bigger (web) projects, I can say that when progressively adding new features and making changes to a project this size, it starts to become a real mess.

In HearthstoneTracker, application features are split into different folders. All the code specific for that feature (view / viewmodel / helpers) go into that folder. You can assume that all the different features are actual plugins for the main application (shell).

Although some features rely on each other (games<->arenas), try to think about the dependencies you create between features if you are going import namespaces from another feature.

In general, features are allowed to reference the application shell and framework, but not other features. Unless the feature is a 'core' feature (e.g. global data, settings and game manager).

### Infrastructure 

All the code responsible for composition, logging and starting up. This binds all the components together, initializes and start the Shell and other systems. This code does not know (a lot) about the actual features in the application. It just starts the shell.

### Framework 

Some common framework and user interface code (Framework / UI / Util), also feature independent (could be shared with other projects). E.g. validation or caliburn helper functions / extensions.

Also, all the UI behaviors, controls and converters.

## Other notes:

 * Views (xaml) usually do **not** have a code-behind file but are automatically bound to a viewmodel. They are found by a naming convention. In you views (xaml), you can use normal and/or caliburn binding expressions to bind to your viewmodel properties and methods (see caliburn documentation or existing code for examples).
 * TODO
