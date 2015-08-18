# API cs.obj.CssNode

### cs.obj.CssNode(configuration)

* **Description**: Constructor for cs.obj.CssDocument. 

* **Parameter**:
    * *Object* configuration - configuration params (if undefined, empty CssNode instance is created)
        * configuration.raw: the java CSSChunk instance
        * configuration.content: a style rule to craete a CssNode instance from (including selector & properties)
        * configuration.type: create a CssNode with one of the types [cs.obj.CssNode.TYPE_SELECTOR|cs.obj.CssNode.TYPE_PROPERTY]

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.addChild(childNode, index)

* **Description**: Insert child at given index. 

* **Parameter**:
    * *cs.obj.CssNode* childNode - node to add as new child
    * *integer* index - position index in list of child nodes

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.appendChild(childNode)

* **Description**: Append child at the end of child list.

* **Parameter**:
    * *cs.obj.CssNode* childNode - node to add as new child

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.clone()

* **Description**: Clone current CssNode instance.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.delete()

* **Description**: Delete the current CssNode instance from tree of CSS nodes.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getChild(index)

* **Description**: Get child node at given position.

* **Parameter**:
    * *integer* index - position index in list of child nodes

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getChildren()

* **Description**: Get all child nodes of current node.

* **Parameter**: none

* **Return**: *array*

### cs.obj.CssNode.prototype.getCSS()

* **Description**: Get the string representation.

* **Parameter**: none

* **Return**: *string*

### cs.obj.CssNode.prototype.getFirstChild()

* **Description**: Get first child.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getPreviousSibling()

* **Description**: Get the previous sibling node.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getLastChild()

* **Description**: Get last child.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getNextSibling()

* **Description**: Get the next sibling node.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getParent()

* **Description**: Get the parent node.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*|*cs.obj.Css*

### cs.obj.CssNode.prototype.getPreviousSibling()

* **Description**: Get the pevious sibling node.

* **Parameter**: none

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.getRootCss()

* **Description**: Get the CssDocument according to the node tree.

* **Parameter**: none

* **Return**: *cs.obj.CssDocument*

### cs.obj.CssNode.prototype.getType()

* **Description**: Get the node type.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.CssNode.prototype.insertBefore()

* **Description**: Insert sibling before this node.

* **Parameter**:
    * *cs.obj.CssNode* siblingNode - node to add as new sibling

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.insertBehind()

* **Description**: Insert sibling behind this node.

* **Parameter**:
    * *cs.obj.CssNode* siblingNode - node to add as new sibling

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.removeChild()

* **Description**: Remove given child node from tree of Css nodes.

* **Parameter**:
    * *cs.obj.CssNode* childNode - child node to remove

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.setContent(content)

* **Description**: Set current CssNode content.

* **Parameter**:
    * *string* content - node content

* **Return**: *cs.obj.CssNode*

### cs.obj.CssNode.prototype.setType(type)

* **Description**: Set the node type to [cs.obj.CssNode.TYPE_SELECTOR|cs.obj.CssNode.TYPE_PROPERTY].

* **Parameter**:
    * *integer* type - node type

* **Return**: *cs.obj.CssNode*