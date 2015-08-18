# API cs.obj.CssDocument

### cs.obj.CssDocument(configuration)

* **Description**: Constructor for cs.obj.CssDocument. 

* **Parameter**:
    * *Object* configuration - configuration params:
        * configuration.raw: the java CSSChunk instance
        * configuration.path: path to css file

* **Return**: *cs.obj.CssDocument*

### cs.obj.CssDocument.prototype.getNodes()

* **Description**: Get all child nodes (1st level). 

* **Parameter**: none

* **Return**: *array*

### cs.obj.CssDocument.prototype.getChildAtCursorPosition()

* **Description**: Get child node at specific position of text file. 

* **Parameter**:
    * *integer* position - position from file start

* **Return**: *cs.obj.CssNode*

### cs.obj.CssDocument.prototype.getFilePath()

* **Description**: Get the file path of current CSS document. 

* **Parameter**: none

* **Return**: *string*

### cs.obj.CssDocument.prototype.getSelectedNodes()

* **Description**: Get selected nodes of current CSS document.

* **Parameter**: none

* **Return**: *array*

### cs.obj.CssDocument.prototype.removeChild()

* **Description**: Remove the child CSS node from tree of CSS nodes.

* **Parameter**:
    * *cs.obj.CssNode* childNode - the child node to remove

* **Return**: *array*