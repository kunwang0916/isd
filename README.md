## Topics

* [Architecture](#Architecture)
* [Design Pattern](#Design-Pattern)
* [UI](#UI)
* [Communications Patterns](#Communications-Patterns)
* [Reactive Programming](#Reactive-Programming)
* [Memory Management](#Memory-Management)
* [Concurrency](#Concurrency)
* [Persist Data](#Persist-Data)
* [Debug](#Debug)
* [Languages](#Languages)
* [Others](#Other)

## Architecture

### MVC

* [Model-View-Controller](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MVC.html)

  ![mvc.png](./resource/img/mvc.png)

### MVVM

* [Model-View-ViewModel](https://www.objc.io/issues/13-architecture/mvvm/)

  ![mvvm.png](./resource/img/mvvm.png)

* MVVM try to solve the issue of "Massive View Controller" by adding a `ViewModel` layer between `Model` and `ViewController`

  1. MVVM is compatible with your existing MVC architecture.
  1. MVVM makes your apps more testable.
  1. MVVM works best with a binding mechanism.

### VIPER

* [View-Interactor-Presenter-Entity-Routing](https://www.objc.io/issues/13-architecture/viper/)
  ![viper.png](./resource/img/viper.png)

* components
  * View: displays what it is told to by the Presenter and relays user input back to the Presenter.
  * Interactor: contains the business logic as specified by a use case.
  * Presenter: contains view logic for preparing content for display (as received from the Interactor) and for reacting to user inputs (by requesting new data from the Interactor).
  * Entity: contains basic model objects used by the Interactor.
  * Routing: contains navigation logic for describing which screens are shown in which order.

### RIBs

* [Router-Interactor-Buider](https://github.com/uber/RIBs)
  * and Presenter, View.
  ![ribs.png](./resource/img/ribs.png)

### Trade Off

#### No Sliver Bullet

There is no **Best Architecuture**, we should choose bewteen the different options based on our use-case, trade-off bewteen `complexity` and `flexibility`. MVC is good for simple & small application/page, MVVC maybe better for mid-size application/page. for large app with complicated business logic, RIBs or VIPER would be good way to go.

#### What is the difference between RIBs and MV*/VIPER

MVC, MVP, MVI, MVVM and VIPER are architecture patterns. RIBs is a framework. What differentiates RIBs from frameworks based on MV*/VIPER is:

* Business logic drives the app, not the view tree. Unlike with MV*/VIPER, a RIB does not have to have a view. This means that the app hierarchy is driven by the business logic, not the view tree.
* Independent business logic and view trees. RIBs decouple how the business logic scopes are structured from view hierarchies. This allows the application to have a deep business logic tree, isolating business logic nodes, while maintaining a shallow view hierarchy making layouts, animations and transitions easy.

## Design Pattern

## UI

## Communications Patterns

## Reactive Programming

## Memory Management

[Memory management](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/MemoryManagement.html) in a Cocoa application that doesn’t use garbage collection is based on a reference counting model. When you create or copy an object, its retain count is 1. Thereafter other objects may express an ownership interest in your object, which increments its retain count. The owners of an object may also relinquish their ownership interest in it, which decrements the retain count. When the retain count becomes zero, the object is deallocated (destroyed).

  ![reference_counting_model.png](./resource/img/reference_counting_model.png)

### Automatic Reference Counting (ARC)

ARC inserts the appropriate retains and releases required for reference counting at compile time, no collector process is needed to continually sweep memory and remove unreferenced objects.

### Retain Cycle / Strong Reference Cycles

For a class instance to be fully deallocated under ARC, it needs to be free of all strong references to it. But there is a chance that you could structure your code in such a way that two instances strongly reference each other and therefore never let each other’s reference count drop down to zero.

### Weak and Unowned

There are two ways of resolving Retain Cycle in Swift: weak references and unowned references.

**Weak reference** is used when you know that a reference is allowed to become nil whereas **unowned reference** is used when you are certain that the reference has a longer lifecycle and will never become nil. Since **weak references** can have a value or no value at all, they must be defined as optional variables. An **unowned reference** has to be defined as non-optional since it is assumed to always have a value.

### Garbage Collection

Runtime detects unused objects and object graphs in the background. This happens at intermediate intervals, either after a certain amount of time has passed or when the runtime memory gets low, and not released at that exact moment.

### ARC vs GC

Both GC and ARC aim to free developer from memory management, though **it doesn't completely free you from worrying about memory management.**

* GC is Runtime will ARC is compile-time.
* ARC is real-time release while frees an object "sometime later".
* GC can cope with retain cycles while ARC can not.
* Typically, **garbage collection** has certain disadvantages, including consuming additional resources, performance impacts, possible stalls in program execution, and incompatibility with manual resource management.

* [Garbage Collection vs Automatic Reference Counting](https://medium.com/computed-comparisons/garbage-collection-vs-automatic-reference-counting-a420bd4c7c81)

## Concurrency

## Persist-Data

## Debug

## Languages

### Swift

### Objective-C

## Other

### Site

* [developer.apple.com/](https://developer.apple.com/)
* [swift.org](https://swift.org/)
* [objc.io](https://www.objc.io)
