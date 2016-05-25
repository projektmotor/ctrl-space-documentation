# The first CTRL+SPACE Blueprint

Writing a Blueprint is not really a rocket science. On this page we will walk through a little tutorial. It'll show
how to create a simple Code Completion Simplifier named `blueprint-tutorial`, which is going to read some Slimage data and generates a bunch of
CSS properties.

## Create a new Blueprint

Creating a new Blueprint is quite simple. Just click on the add button inside the Blueprint Explorer window and enter a
name for the Blueprint.

![First CTRL+SPACE Blueprint - create](/images/first_blueprint_create_button.png "First CTRL+SPACE Blueprint - create")
![First CTRL+SPACE Blueprint - set name](/images/first_blueprint_create_name.png "First CTRL+SPACE Blueprint - set name")

The Blueprint Explorer tree is reloaded afterwards. Expand the `blueprints` node and you will see your created blueprint
as a new tree node.

### Blueprint Structure

You may have already noticed that the new Blueprint is not just a single file. Every Blueprints has a base structure, which 
consists of:

![First CTRL+SPACE Blueprint - the structure](/images/first_blueprint_structure.png "First CTRL+SPACE Blueprint - the structure")

* a list of executable simplifiers (provided by Clickable Simplifiers)
* `files` folder which contains
    * `manifest.csm` file specifying some metadata like Blueprint version and Blueprint engine version
    * `main.js` point to hook in business logic

> **Note:** The simplifier `simplifier sample` would not be created in your case. It is just shown fpr demonstration purposes.

## Extend CTRL+SPACE Code Completions

Now all the groundwork is done, we can start adding some logic. In our case we would like to extend the CSS code completions
to add width & height of a layer in one step. Therefor open the the `main.js` file and extend the code completions by adding
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