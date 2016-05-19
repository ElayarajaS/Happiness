Objective-C Compatibility, property List

Custom Views
So how do I implement my drawRect?
Core Graphics Concepts

UIBezierPath

Create a UIBezierPath
let path = UIBEsizerPath()
Move around , add line or arcs to the path
path.moveToPoint(CGPoint(80, 50)) //assume screen is 160 *250
path addLineToPoint(CGPoint(140, 150))
path.addLinrToPoint(CGPoint(10, 150))
Close the path (if you want)
path.closePath()
Now that you have a path, set attributes and stoke/fill
UIColor.greeenColor().setFill()
UIColor.redColor().setStroke()
path.lineWith = 3.0
path.fill()
path.stroke()

Drawing

You can draw common shape with UIBenzierPath
Clipping your drawing to a UIBezierPath’s Path
Hit detection

UIColor

Color are set using UIColor
Background color of a UIView
Color can have alpha(transparency)
If you want to draw in your view with transparency
You can make your entire UIView transparent

Drawing Text

Usually we use a UILabel to put text on screen
To draw in drawRect, use NSAttributedString
Mutability is done with NSMutableAttributedString
NSAttributedString is not a String, nor an NSString
Attributed String
Setting attributed on an attributed string
Attributes

Fonts

Fonts in iOS 7 and later are very important to get right

Drawing Images

There is a UILabel-equivalent for images
Creating a UIImage object
You also create one from files in the file system
you can even create one by drawing with core Graphics
Redraw on bounds change?
By default, when a UIView’s bounds changes, there in no redraw
UIViewContentMode

Demo



Protocols and Delegation

Interface Builder
Demo: Viewing and Editing your custom UIViews in Your storyboard (FaceView)
The Happiness MVC’s Model
It’s happiness, of course! (which is different from sliminess)
Protocols and Delegation
How can generic UIView not ”own their data” and still draw that data?
Demo: Showing the Happiness MVC’s Model using generic FaceView in this View

Gestures

Demo: Happiness pinch and pan
Multiple MVCs (time permitting)
Split View Controllers & Navigation Controllers & Tab Bar Controllers
Segues
Popovers


Extensions

Miscellaneous topic!
You can add methods and properties to a class (even if you don’t have the source).
There are some restrictions
You can’t re-impliment methods or properties that are already there ( only add new ones ).
This properties you add can have no storage associated with them.
This features is easily abused
It should be used to add clarity to readability not obfuscation!
Don’t use it as a substitute for good object-oriented design technique.
Best used (at least for beginners) for very small, well-contained helper functions.
can actually be used well to organise code but required architectural commitment.
When in doubt (for now), don’t do it.

Protocols

A way to express an API minimally
Instead of forcing the caller to pass a class/struct, we can ask for specifically what we want
We just specify the properties and methods needed
A protocol is a TYPE just like any other type, except ..
It has no storage or implementation associated with it
Any storage or implimentation required to implement the protocol is in an implementing type
An implementing type can be any class, struct or enum
Otherwise, a protocol can be used as a to declare variables, as a functions parameter, etc.
There are three aspects to a protocol
The protocols declaration (what properties and methods are in the protocol)
The declaration where a class, struct or enum says that it implements a protocol
The actual implementation of the protocol in said class, struct or enum

Delegation


A very important use of protocols
It’s how can implement “blind communication” between a view and its Controller
How it play out ..
create a delegation protocol (defines what the View want the Controller to take care of)
Create a delegate property in the View to get/do things it can’t own or control
Use the delegate property that it implement the protocol
Controller sets self as the delegate of the View by setting the property in #2 above
Implement the protocol in the Controller
Now the View is hooked up to the Controller
But the View still has idea what the Controller is, so the View remains generic/reusable

Demo


Gestures

We will see how to draw in a UIView, how do we get touches?
We can get notified of the raw touch events (touch down, moved, up, etc.)
Or we can react to certain, predefined “gestures”. The later is the way to go!
Gestures are recognised by instances of UIGestureRecognizer
The base class is “abstract”. We only actually use concrete subclasses to recognise.

There are TWO sides to using a gesture recogniser
1. Adding a gesture recogniser to a UIView (asking the UIView to “recognise” that gesture)
2. Providing a method to “handle” that gesture (not necessarily handled by the UIView)
Usually the First is done by a Controller
Through occasionally a UIView will do this itself if the gesture is integral to its existence
The Second is provided either by the UIView or a Controller
Depending on the situation. We will see an example of both in our demo.


Demo
FaceView Gestures
Add a gesture recogniser (pinch) to the FaceView to zoom in and out (control its own scale)
Add a gesture recogniser (pan) to the faceView to control happiness (Model) in the Controller










