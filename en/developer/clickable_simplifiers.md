# CTRL+SPACE Clickable Simplifiers

Clickable Simplifiers are very useful if you want to automate complex tasks. These tasks could either end up in multiple
changes or do some background work which doesn't effect your project files directly. To execute those Blueprints the user
has to select them inside the Blueprint Explorer and double click it.

This chapter assumes that you already know how to add a new Blueprint. If this is not the case please read 
chapter [First Blueprint](/en/developer/first_blueprint.md).
 
## Add new Clickable Simplifiers

To add a new Clickable Simplifier to the list of Simplifiers the `cs.extend.addSimplifier()` method has to be called in the main.js file (or an included file).

```JavaScript
cs.extend.addSimplifier({
    name: 'simplifier-name',
    onRun: function() {}
});
```

Two parameters:

* `name`: name of the code completion (occurs in the list of available Blueprints)
* `onRun`: callback executed when the user runs the Clickable Simplifier

## Working with the Model

To edit, add or remove some of your source code using **Clickable Simplifiers, you should work with the files object 
representation instead - the model.** Similar like the `cs.obj.SmallLayeredImage` object, there is a model object 
representing the source code files. The following objects are currently available:

* `cs.obj.CssDocument` with multiple `cs.obj.CssNode` (as tree)
* `cs.obj.HtmlDocument` with multiple `cs.obj.HtmlNode` (as tree)

More file types coming soon!

After the execution of the Clickable Simplifier has finished, the model is rendered back into source code files.

### CSS Model

Working with the CSS model normally needs two file objects: [`cs.obj.CssDocument`](/en/developer/api/cs.obj.CssDocument.md)
and [`cs.obj.CssNode`](/en/developer/api/cs.obj.CssNode.md), where the `cs.obj.CssNode` objects are child elements of
`cs.obj.CssDocument` and of itself.

> **NOTICE**: A CSS node could either be a selector or a styling property.

#### Tree Traversal

Sometimes traversal through the tree of CSS nodes becomes necessary. The following methods will give you the possibility 
to get children, siblings and parent nodes.

* `node.getParent()`: get parent node of a CSS node
* `node.getNextSibling()`: get next closest sibling of a CSS node
* `node.getPreviousSibling()`: get previous closest sibling of a CSS node
* `node.getChild(index)`: get child at given position
* `node.getChildren()`: get array of all child nodes
* `node.getFirstChild()`: get the first child of a CSS node
* `node.getLastChild()`: get the last child of a CSS node

#### Getting the Selected CSS Node

One very common use of the `css.obj.CssDocument` object is to edit, add or remove some of its nodes (`cs.obj.CssNode` instances). 
To do this, you first have to get a node to work with. In most cases the user should select these node(s) before the
Blueprint execution. The Clickable Simplifier can make use of these selections.

```JavaScript
var
    activeCss = cs.panel.css.getActiveCss();
    selectedNodes = activeCss.getSelectedNodes();
```

* `cs.panel.css.getActiveCss()`: retrieve the active CSS document (cs.obj.CssDocument)
* `activeCss.getSelectedNodes()`: retrieve selected CSS nodes (cs.obj.CssNode) as array from active CSS document 

Of course you can walk through any CssDocument instance and make use of the tree traversal methods
(DOM: getNextSibling(), getChildren(), ...) to get the CSS node you need. See chapter [Tree Traversal](#Tree_Traversal) for
more details.

#### Adding a new CSS Node

Similar to node retrieval, you first have to retrieve the position where to add the new CSS node in your document. After doing this, you
want to determine the child or sibling position. And last but not least you need a `cs.obj.CssNode` instance to add. Let's 
have a look on a little example.
 
```JavaScript
var
    selectedNodes = cs.panel.css.getActiveCss().getSelectedNodes(),
    insertNode = new cs.obj.CssNode({content: ".ctrl-space-tutorial {\n\tfont-size:1.1em;\n}"});

for (var index in selectedNodes) {
    if (selectedNodes[index].getType() === cs.obj.CssNode.TYPE_SELECTOR) {
        selectedNodes[index].insertBehind(insertNode.clone());
    }
}
```

* `new cs.obj.CssNode()`: create a new cs.obj.CssNode instance (and children) by parsing the `content` property
* `if (selectedNodes[index].getType() === cs.obj.CssNode.TYPE_SELECTOR) {}`: only add sibling if selected node is a selector
* `selectedNodes[index].insertBehind(insertNode.clone())`: add clone of `insertedNode` as new sibling of current node

#### Editing a CSS Node

The editing of a CSS node is not very difficult. You just have to retrieve the node you want to edit, perform some updates
on its content und write this content back to the CSS node.
 
The following example, reads the selected property nodes and adds a `;` if this is not yet present.  

```JavaScript
var
    selectedNodes = cs.panel.css.getActiveCss().getSelectedNodes(),
    nodeContent;

for (var index in selectedNodes) {
    if (selectedNodes[index].getType() !== cs.obj.CssNode.TYPE_PROPERTY) {
        continue;
    }
    
    nodeContent = selectedNodes[index].getCSS();
    
    if (nodeContent.substr(stralt.length-1, 1) !== ';') {
        nodeContent += ';';
        selectedNodes[index].setContent(nodeContent);
    }
}
```

* `selectedNodes[index].getCSS()`: retrieve the node content as string
* `selectedNodes[index].setContent(nodeContent)`: set updated string as new node content 

#### Removing a CSS Node

Let's get to the point of CSS node removal. Similar like editing, you first should get the node to delete. Once this is
done, the `delete()` method would do the job.

```JavaScript
var
    selectedNodes = cs.panel.css.getActiveCss().getSelectedNodes();

for (var index in selectedNodes) {
     selectedNodes[index].delete();
}
```

* `selectedNodes[index].delete()`: deletes the cs.obj.CssNode instance from tree of CSS nodes

Many ways lead to Rome. Of course there are multiple solutions to get this done. Alternatively you can use the
`removeChild()` & `removeChildAtIndex()` methods. See [Developer > API > cs.obj.CssNode](/en/developer/api/cs.obj.CssNode.md)
for more details.

### HTML Model

Similar to the CSS handling, there exist two model classes (`cs.obj.HtmlDocument` and `cs.obj.HtmlNode`) to work with.
The `cs.obj.HtmlDocument` holds some meta data (like file path) and links to a tree of `cs.obj.HtmlNode` (DOM). The 
`cs.obj.HtmlNode` instances contain a self reference to link child and parent nodes.
  
#### Tree Traversal
 
The traversal of a HTML document can be done by simple DOM methods like `getChild()`, `getParent()`, which are
equal to the CSS traversing methods (both based on the same model)

* `node.getParent()`: get parent node of a HTML node
* `node.getNextSibling()`: get next closest sibling of a HTML node
* `node.getPreviousSibling()`: get previous closest sibling of a HTML node
* `node.getChild(index)`: get child at given position
* `node.getChildren()`: get array of all child nodes
* `node.getFirstChild()`: get the first child of a HTML node
* `node.getLastChild()`: get the last child of a HTML node

To make use of CSS selectors you first need the file object `cs.obj.HtmlDocument`. Calling the `getChildrenByCSS()` on it gives
you all the nodes matching your selector string.

```JavaScript
var
    activeDocument = cs.panel.html.getActiveHtml(),
    headlines = activeDocument.getChildrenByCSS('h1');
```

#### Getting the Selected HTML Nodes
 
Your Blueprint should do some operations on a node which was selected by the user before? To achieve this, you should go
a similar way like retrieving the selected CSS node. Use the `cs.panel.html` class to get the active HTML document. Once
you have done this, call `getSelectedNodes()` and you are fine.

```JavaScript
var
    activeDocument = cs.panel.html.getActiveHtml(),
    selectedNodes = activeDocument.getSelectedNodes();
```
 
#### Adding new HTML Nodes
 
Before adding a node you should have to create it. The constructor of `cs.obj.HtmlNode` gets a single object as parameter.
Depending on the properties, the parameter object triggers different ways of creating a new instance. One possibility is 
parsing a given HTML string into a new `cs.obj.HtmlNode` instance.

```JavaScript
var
    node = cs.obj.HtmlNode({content: '<a href="#">anchor-link</a>'});
```

The node can easily be added to the tree with one of the following methods:

* `appendChild()`: append node to list of child nodes
* `insertChild(index)`: insert node to list of child nodes at given position
* `insertBefore()`: insert node to list of sibling nodes before current node
* `insertBehind()`: insert node to list of sibling nodes behind current node

```JavaScript
var
    node = cs.obj.HtmlNode({content: '<a href="#">anchor-link</a>'}),
    selectedNodes =  cs.panel.html.getActiveHtml().getSelectedNodes();

for (var index in selectedNodes) {
    selectedNodes[index].insertBehind(node.clone());
}
```

#### Editing HTML Nodes
 
There are several cases why you want to edit a HTML node.

* changing the tag name
* edit attributes and attribute values
* updating the node text

Of course you first have to retrieve your HTML node you want to work with. Afterwards just call a method like `setAttribute()` (full
list under [Developer > API > cs.obj.HtmlNode](/en/developer/api/cs.obj.HtmlNode.md).

```JavaScript
var
    selectedNodes =  cs.panel.html.getActiveHtml().getSelectedNodes();

for (var index in selectedNodes) {
    selectedNodes[index].setNodeName('div');
    selectedNodes[index].setAttribute('class', '.ctr-space');
    selectedNodes[index].setHtml('this is html content');
}
```

This example transforms all selected HTML nodes into `div` tags with the class `.ctrl-space` and adds the text content
`this is html content`.

#### Removing HTML Nodes
 
Like removing CSS nodes, removing HTML nodes is very simple too. Get your HTML node you want to remove and
call `delete()` on it.

```JavaScript
var
    selectedNodes =  cs.panel.html.getActiveHtml().getSelectedNodes();

for (var index in selectedNodes) {
    selectedNodes[index].delete();
}
```