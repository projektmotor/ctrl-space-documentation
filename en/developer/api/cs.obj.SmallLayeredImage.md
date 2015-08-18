# API cs.obj.HtmlDocument

### cs.obj.SmallLayeredImage(configuration)

* **Description**: Constructor for cs.obj.SmallLayeredImage. Could be used with optional configuration parameter. If no param is given, empty Slimage is created. 

* **Parameter**:
    * *Object* configuration - configuration params:
        * configuration.raw: the java SmallLayersImage instance
        * configuration.width: the java SlimLayer instance
        * configuration.height: optional max width for image
        * configuration.path: path to source image (if width/height is set: jpeg/gif/png, otherwise: slim)

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.export(path, name)

* **Description**: Export SmallLayeredImage to common image (png/jpeg/...). 

* **Parameter**:
    * *string* path: file path
    * *string* name: file name

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.getLayerRoot()

* **Description**: Get root SlimLayer of SmallLayeredImage.

* **Parameter**: none

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.getLayers()

* **Description**: Get all layers of current SmallLayeredImage instance.

* **Parameter**: none

* **Return**: *array*

### cs.obj.SmallLayeredImage.prototype.getPath()

* **Description**: Get path of SmallLayeredImage file. 

* **Parameter**: none

* **Return**: *string*

### cs.obj.SmallLayeredImage.prototype.getSelectedLayers()

* **Description**: Get the currently selected layers.

* **Parameter**: none

* **Return**: *array*

### cs.obj.SmallLayeredImage.prototype.mergeAll()

* **Description**: Merge all layers in layer tree into new one.

* **Parameter**: none

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.save()

* **Description**: Saves SmallLayeredImage to filesystem. If `filePath` & `fileName` is set, SmallLayeredImage will be saved at the new path.

* **Parameter**:
    * *string|null* path: file path
    * *string|null* name: file name

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.setLayerRoot()

* **Description**: Set a new layer as root of node tree.

* **Parameter**:
    * *cs.ob.SlimLayer* slimLayer: new layer to use for tree root

* **Return**: *cs.obj.SmallLayeredImage*

### cs.obj.SmallLayeredImage.prototype.setPath()

* **Description**: Set path of SmallLayeredImage file.

* **Parameter**:
    * *string|null* path: file path
    * *string|null* name: file name

* **Return**: *cs.obj.SmallLayeredImage*