
# What is a CTRL+SPACE Blueprint? #

You know Smartphone apps? Good, Blueprints are like apps that extend the Smartphone OS, though they are not running on an Operating System but on an IDE! The IDE is the OS.

Blueprints are basically folders containing JavaScript files.
By decaration, it has to contain a main.js file containing the startup code.

With that code you can extend parts of the IDE and automate your daily tasks.

A Blueprint is made of so called Simplifiers - JavaScript functions. They're called Simplifiers because they mostly simplify things and can be seen as small extensions of the IDE.

So its this Hierarchy:

* Blueprint Library
    * Blueprint A
        * Simplifier A1
        * Simplifier A2
    * Blueprint B
        * ...

## Code Completion Simplifiers ##

A Completion Simplifier extends the code completion window of a certain editor (HTML/CSS) and lets you implement your own tools.
When you hit ctrl+space inside an HTML/CSS editor, a code completion window appears. With CC Simplifiers appear there, too. You can insert code at the current caret position that was generated via JavaScript.
The Blueprint API provides access to opened files and their models as well a selections and many other things (see [Developer doc](/developer/api/index.md))

![Execute Blueprints by Code Completion](/images/sbl_code_completion_simplifier.png)

> **Note:** Code Completions Simplifier are bound to a mime type, if you can't see your simplifier, make sure you've set the correct mime type.

## Clickable Simplifiers  ##

The other kind of Simplifier is a clickable one. It's just a small JS function, like Code Completion Simplifiers, but will appear as a small "play" icon inside the Blueprint Explorer Tree under your Blueprint node.
you can launch the containg script by simply double click on the play icon.

![Execute clickable simplifiers](/images/sbl_clickable_simplifier.png)

If not done yet, you can open the Blueprint Explorer via `Window > Blueprint Explorer`.

## The Standard Blueprint Library (SBL) ##

To enjoy the power of CTRL+SPACE, the basic version comes with some predefined Blueprints - the Standard Blueprint Library.
They cover very basic usescases, for example reading a margin value from a CSImage file or create images from it.
You can see all currently available Blueprints of the SBL down on this page.

### Code Completion (CSS) ###

|Background||
|-|-|
| **background-color (HEX)** | get the layer color as HEX value (e.g. background-color: #000000; |
| **background-color (RGB)** | get the layer color as RGB value (e.g. background-color: rgb(0,0,0); |
| **background-image** | save the layer as background image and write a css property including the path (e.g. background-image: url(/images/example.jpg); |

|Dimension||
|-|-|
| **width** | get width of the selected layer (e.g. width: 100px;) |
| **height** | get width of the selected layer (e.g. height: 100px;) |

|FONT||
|-|-|
| **font-family** | get font name of the selected layer (e.g. font-family: Arial; |
| **font-color** | get font color of the selected layer (e.g. font-color: rgb(0,0,0); |

|Margin||
|-|-|
| **margin-left** | get left margin of one layer to left image border order between two layers |
| **margin-right** | get right margin of one layer to right image border order between two layers |
| **margin-top** | get top margin of one layer to top image border order between two layers |
| **margin-bottom** | get bottom margin of one layer to bottom image border order between two layers |

|Padding||
|-|-|
| **padding-left** | get left padding of one layer to left image border order between two layers |
| **padding-right** | get right padding of one layer to right image border order between two layers |
| **padding-top** | get top padding of one layer to top image border order between two layers |
| **padding-bottom** | get bottom padding of one layer to bottom image border order between two layers |

|Position||
|-|-|
| **left** | get left offset of one layer to left image border order between two layers |
| **right** | get right offset of one layer to right image border order between two layers |
| **top** | get top offset of one layer to top image border order between two layers |
| **bottom** | get bottom offset of one layer to bottom image border order between two layers |

Of course this library does not cover your custom business processes. If you come to the point where the SBL is not enough
for you, read the chapter about writing your own Blueprints. This is not a rocket science ;)