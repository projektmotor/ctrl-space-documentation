# Ctrl-Space Code Completion Simplifiers

With CC Simplifiers you can insert code directly at the cursor position or you can just launch any code you want without inserting.
Or access the underlying DOM of the current file and do your modifications there.

This chapter assumes that you already know how to add a new Blueprint. If this is not the case please read 
chapter [First Blueprint](/en/developer/first_blueprint.md).

## Extend Code Completions

To extend the default code completions call the `cs.extend.addAutocompletion()` method.

```JavaScript
cs.extend.addAutocompletion({
    name : 'code-completion-name',
    scope : 'text/css',
    onSelect : function(completionObject) {},
    onBlur : function() {},
    onSubmit : function() {}
});
```

It gets one object as parameter, containing the following keys:

* `name`: name of the code completion (occurs in the list of available Blueprints)
* `scope`: mime type where the code completion should be available in (e.g. 'text/css', 'text/html')
* `onSelect`: callback executed when the user selects the code completion
* `onBlur`: callback executed when the user leaves the selected code completion
* `onSubmit`: callback executed when the user executes the code completion (hit return key or double click)

### Set the Mime Type

By setting the mime type of the Code Completion Simplifier, you decide where the Simplifier should be available. Currently
it is possible to extend code completions for the following mime types:

* `text/css`
* `text/html`

If you like to extend code completions for other mime types, please tell us! 

### Callbacks onSelect & onBlur
 
These callbacks are very well suited for showing the user some extra information on what happens if he is going to execute
the Blueprint. For example by showing some extra information inside the SlimageViewer or write something to the output
window.

```JavaScript
cs.extend.addAutocompletion({
    name : 'code-completion-name',
    scope : 'text/css',
    onSelect : function(completionObject) {
        cs.panel.image.drawLine(10, 10, 100, 10, "this is a label text");
    },
    onBlur : function() {
        cs.panel.image.clear()
    },
    onSubmit : function() {}
});
```

### Callback onSubmit
 
These callback is the heart of Code Completion Simplifiers. Everything you want write at the cursor position (where the
user opened the code completion) should returned here.

```JavaScript
cs.extend.addAutocompletion({
    name : 'code-completion-name',
    scope : 'text/css',
    onSelect : function(completionObject) {},
    onBlur : function() {},
    onSubmit : function() {
        return 'margin-top: 20px';
    }
});
```