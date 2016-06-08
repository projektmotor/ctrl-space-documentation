# Working with CSImages and the CSImageViewer

What is a **S**mall **L**ayerd **Image** (CSImage)? A CSImage is a file representing layered graphics resources. It could
either be build by converting Photoshop files to CSImages, or by creating a blank CSImage via the Blueprint API. Other input
formats like Adobe Ilustrator coming soon!

According to the CSImage files the Blueprint API provides a object called `cs.obj.SmallLayeredImage`. This object
allows you to work with CSImages, for example getting the selected layer and extract its style informations.

## CSImage & SlimLayer Structure

### CSImage

A CSImage instance consists of some meta data and a SlimLayer tree. The meta data could be used to store document wide information
like author, title and keywords. To access or set these data just use the `getMeta***()` or `setMeta***()` methods 
in your SmallLayeredImage instance (see [cs.obj.SmallLayeredImage](/en/developer/api/cs.obj.SmallLayeredImage.md)). 

### CSImage Layer Tree

The SlimLayer tree is a parent-child linked collection of SlimLayers (see [cs.obj.SlimLayer](/en/developer/api/cs.obj.SlimLayer.md)). 
Its root node is connected to the CSImage instance and could be accessed by calling `CSImage.getLayerRoot()`. Methods for tree traversing
like `getChildLayers()` & `getParent()` are provided by the SlimLayer object itself.

### SlimLayers

SlimLayers hold most of the styling data. They could be used to get dimensions, position, colors and a lot of other
information (see [cs.obj.SlimLayer](/en/developer/api/cs.obj.SlimLayer.md)).

How to get a SlimLayer out of the layer tree? The answer is not quite simple and depends on your needs. One way is to 
fetch the root node and make use of the SlimLayer tree traversing methods.

```JavaScript
var 
    rootNode = CSImage.getLayerRoot(),
    firstLevel = rootNode.getChildLayers();
    
for (var i in firstLevel) {
    if (firstLevel[i].getBottom() >= 100) {
        // do some stuff
    }
}
```

It is also possible to get the layer stack for a given position of the CSImageViewer.

```JavaScript
var 
    layerStack = CSImage.getLayerStackAt(100, 100); // get layer stack at x=100, y=100 of CSImageViewer
    
for (var i in layerStack) {
    if (layerStack[i].hasText()) {
        // do some stuff
    }
}
```

The most common way is to get the selected SlimLayer(s). To achieve this, just call the `getSelectedLayers()`
method of the CSImage.

```JavaScript
var 
    selectedLayers = CSImage.getSelectedLayers();
    
for (var i in selectedLayers) {
    if (selectedLayers[i].hasText()) {
        // do some stuff
    }
}
```

## Creating CSImage Instances

CTRL+SPACE could be used in two directions. The first (and common) one is to open/import any kind of CSImage and hydrate
all the information you need into your template. The other one is to produce some graphics, based on a set of rules, and store it
as CSImage or regular image file (JPEG, PNG, GIF). For example if you have to generate similar banners
over and over again, you can write the rules as a Blueprint and let CTRL+SPACE generate all your banners.

The creation of new CSImage instances could be done in multiple ways. This depends on your input data.

### Create CSImage Instance from CSImage File

Getting a new CSImage instance based on CSImage file is quite simple. Just call the `CSImage` constructor and set the
`path` parameter.

```JavaScript
var image = new cs.obj.SmallLayeredImage({path: "path/to/CSImage/file.slim"});
```

### Create Empty CSImage Instance

To create a new and empty CSImage instance, you just have to call:

```JavaScript
var myImage = cs.obj.SmallLayeredImage();
```

### Create CSImage Instance from Graphics Source

Another possibility to create new CSImages is to use a simple image file (GIF, JPEG, PNG). Using this way you will get
a new CSImage object which only consists of **one** layer, the root layer.

```JavaScript
var myImage = cs.obj.SmallLayeredImage({
    path: "path/to/CSImage/file.jpg",
    width: 100px,
    height: 100px
});
```

## Working with the CSImageViewer

The CSImageViewer is a component to display CSImages (wow nobody of you would have guessed this ;)). It provides the
possibility to get user input based on CSImages. For example the user has selected a SlimLayer and you want to hydrate
information from it.

Furthermore it is possible to paint elements like lines, rectangles and alpha numeric characters on top of the opened 
CSImage. This may be useful if you want to display the user some extra information on what he is exactly doing right now.
A nice example might be the margin/padding/position Blueprints of the [Standard Blueprint Library (SBL)](/en/user/standard_blueprint_library.md).


### Get the Active CSImage

To get a layer which was previously selected inside the CSImageViewer, you first have to get the active CSImage. The Blueprint
API gives you a possibility to get these active CSImage, by calling `cs.panel.image.getActiveCSImage()`. Once you got your
active CSImage, you can call `getSelectedLayers()`, like on every other CSImage.
 
```JavaScript
var
    selectedLayers = cs.panel.image.getActiveCSImage().getSelectedLayers();
```

### Use for Painting

Starting point to execute paint actions inside a CSImageViewer is the `cs.panel.image` class, which contains all the
painting methods. Using this methods is quite simple, you only need the basic geometric information. If you want to draw
a horizontal, labeled line from P1(100, 100) to P2(100, 200) for example, you can do something like this:

```JavaScript
cs.panel.image.drawLine(
    100,                    // start x value
    100,                    // start y value
    100,                    // end y value
    200                     // end y value,
    'This is my line label'
);
```

If you want to clear all your paintings afterwards, just call `cs.panel.image.clear()`. See [cs.panel.image](/en/developer/api/cs.panel.image.md) 
for a complete list of painting methods.