# API cs.obj.HtmlNode

### cs.obj.HtmlNode(configuration)

* **Description**: Constructor for cs.obj.HtmlNode.

* **Parameter**:
    * *Object* configuration - configuration params
        * configuration.raw: the java CSSChunk instance
        * configuration.content: html string which is parsed to cs.obj.HtmlNode

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.appendChild(childNode)

* **Description**: Appends childNode to list of children.

* **Parameter**:
    * *cs.obj.HtmlNode* childNode - node to add as new child

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.clone()

* **Description**: Clone current HtmlNode instance.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.delete()

* **Description**: Deletes current HTML node instance.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getChild(index)

* **Description**: Get the child node at given index.

* **Parameter**:
    * *integer* index - node index in list of cild nodes

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getChildren()

* **Description**: Get all children (1st level) of the current HtmlNode instance.

* **Parameter**: none

* **Return**: *array*

### cs.obj.HtmlNode.prototype.getFirstChild()

* **Description**: Get the first child node.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getHtml()

* **Description**: Get the nodes text representation.

* **Parameter**: none

* **Return**: *string*

### cs.obj.HtmlNode.prototype.getHtmlDocument()

* **Description**: Get the HtmlDocument instance according to node tree.

* **Parameter**: none

* **Return**: *cs.obj.HtmlDocument*

### cs.obj.HtmlNode.prototype.getLastChild()

* **Description**: Get the last child node.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getNextSibling()

* **Description**: Get next sibling for current HtmlNode instance.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getTagName()

* **Description**: Get the name of current tag (li, a, ...).

* **Parameter**: none

* **Return**: *string*

### cs.obj.HtmlNode.prototype.getParent()

* **Description**: Get the parent node of the current HtmlNode instance.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getPreviousSibling()

* **Description**: Get previous sibling for current HtmlNode instance.

* **Parameter**: none

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.getRawNode()

* **Description**: Get the raw html node (for internal use).

* **Parameter**: none

* **Return**: *Packages.de.projektmotor.blueprint.api.JSDocument*

### cs.obj.HtmlNode.prototype.insertBefore(siblingNode)

* **Description**: Insert node as sibling before current node.

* **Parameter**:
    * *cs.obj.HtmlNode* siblingNode - node to add as new sibling

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.insertBehind(siblingNode)

* **Description**: Insert node as sibling behind current node.

* **Parameter**:
    * *cs.obj.HtmlNode* siblingNode - node to add as new sibling

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.insertChild(childNode, index)

* **Description**: Insert node as child at given position.

* **Parameter**:
    * *cs.obj.HtmlNode* childNode - node to add as new child
    * *integer* index - index in list of children

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.removeAttribute(name)

* **Description**: Remove attribute given by name.

* **Parameter**:
    * *string* name - attribute to remove

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.setAttribute(name, value)

* **Description**: Set attribute given by name to value.

* **Parameter**:
    * *string* name - name of attribute to set 
    * *string* value - attribute value 

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.setHtml(html)

* **Description**: Set HTML of current node.

* **Parameter**:
    * *string* html - html compilant string

* **Return**: *cs.obj.HtmlNode*

### cs.obj.HtmlNode.prototype.setTagName(name)

* **Description**: Set the name of current tag (a, li, ...).

* **Parameter**:
    * *string* name - tag name

* **Return**: *cs.obj.HtmlNode*