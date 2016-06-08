# The first CTRL+SPACE Blueprint

Writing a Blueprint is not really a rocket science. On this page we will walk through a little tutorial. It'll show
how to create a simple Code Completion Simplifier named `blueprint-tutorial`, which is going to read some Slimage data and generates a bunch of
CSS properties.

## Create a new Blueprint

Click File->new Project. Select "CTRLSPACE->CTRL+SPACE Blueprint Library Project" and enter all necessary information. 

A new projects opens up.

Right click on the project, click "Create Blueprint" in the context menu.
Enter the fully qualified Blueprint name in the popup input.
For Example: org.cs.SampleBlueprint will create a main.js file in public_html/org/cs/SampleBlueprint/main.js.

### Blueprint Structure

A Blueprint is alway contained inside a Blueprint Library Project which is basically a NetBeans HTML5 Project with some special options like loading priority which tells the blueprint engine when to load the Library - either at the initial stage or later. A Bleurpint Library on initial stage is called a bridge library because that's the place to wrap up the underlying Java API and provide global variables for all secondary libraries.

## Extend CTRL+SPACE Code Completions

Now all the groundwork is done, we can start adding some logic. In our case we would like to extend the CSS code completions.
To add width & height of a layer in one step. Therefor open the the `main.js` file and extend the code completions by adding
the folling JavaScript.
 
```javascript
/* global cs */

cs.extend.addAutocompletion({
    name : 'width-height',
    scope : 'text/css',
    onSelect : function(completionObject) {},
    onBlur : function() {},
    onSubmit : function() {}
});
```

We extended the code completions by calling the `cs.extend.addAutocompletion` method. For details go to [Code Completion Simplifier](/en/developer/code_completion_simplifiers.md).

The only thing we have to do now, is reloading the Blueprint library and our new Blueprint will be available in any CSS
editor window. 

![First CTRL+SPACE Blueprint - code completion](/images/first_blueprint_code_completion_available.png "First CTRL+SPACE Blueprint - code completion")

> **Note:** Every time you changed a Blueprint, you have to reload the Blueprint Library to let the changes take effect.

## Extract Layer information

Our Code Completion Simplifiers is available now. We can start extracting some layer information and generate CSS properties
according to the information.

To achieve this we have to edit the `onSubmit` callback and add some code like this:

```javascript
/* global cs */

cs.extend.addAutocompletion({
    name : 'width-height',
    scope : 'text/css',
    onSelect : function(completionObject) {},
    onBlur : function() {},
    onSubmit : function() {
        var
            layers = cs.panel.image.getActiveSlimage().getSelectedLayers(),
            layer,
            cssContent = '';
        
        if (!layers || layers.length !== 1) {
            return "";
        }

        layer = layers[0];

        cssContent = cssContent + "width: "+layer.getWidth()+"px;";
        cssContent = cssContent + "\n";
        cssContent = cssContent + "height: "+layer.getHeight()+"px;";

        return cssContent;
   }
});
```

What do we do in here? First we get the currently selected layers by calling `cs.layers.select.active()`. Now we have to do some
result validation and fetch the first (and only) selected layer. Afterwards we just need to build the property string based on the
layer's width and height (`layer.getWidth()`, `layer.getHeight()`). To write the property string into our CSS file, we have
to return it.

That's it! Your first Blueprint is created. Rocket science?

Want to learn more about extracting layer data? Go on reading the [Slimages & SlimageViewer](/en/developer/slimages_and_slimage_viewer.md)
chapter.
