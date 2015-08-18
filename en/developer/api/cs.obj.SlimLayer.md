# API cs.obj.SlimLayer

### cs.obj.SlimLayer(configuration)

* **Description**: Constructor for cs.obj.SlimLayer. Could be used with `raw`, `imagePath` or `width` & `height` property. Shadow & glow properties only used in combination with `imagePath` property.

* **Parameter**:
    * *Object* configuration - configuration params
        * configuration.raw: the java SlimLayer instance
        * configuration.imagePath: java SlimLayer instance (for internal use)
            * configuration.maxWidth: optional max width for image
            * configuration.maxHeight: optional max height for image
            * configuration.shadow.size: shadow size
            * configuration.shadow.offsetX: vertical shadow offset
            * configuration.shadow.offsetY: horizontal shadow offset
            * configuration.shadow.color: shadow color
            * configuration.glow.width: horizontal glow
            * configuration.glow.height: vertical glow
        * configuration.width: layer width
        * configuration.height: layer height
        * configuration.color: layer background color

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.addChild(slimLayer, index)

* **Description**: Add new child to current SlimLayer.

* **Parameter**:
    * *cs.obj.SlimLayer* childLayer - layer to add as new child
    * *integer* index - position in list of child layers (0: at top of layer stack|null: at bottom|integer: at position)

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.contains(x, y)

* **Description**: Check if given coordinates are inside layer bounds.

* **Parameter**:
    * *integer* x - vertical direction
    * *integer* y - horizontal direction

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.copy(x, y)

* **Description**: Copy the current SlimLayer instance.

* **Parameter**: none

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.drawRectangle(offsetX, offsetY, width, height, color, rotation)

* **Description**: Draw rectangle with Java AWT in layer.

* **Parameter**:
    * *integer* offsetX - vertical offset
    * *integer* offsetY - horizontal offset
    * *integer* width - vertical size
    * *integer* height - horizontal size
    * *object* color - background color
    * *rotation* double - rotation angle

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.drawRectangleFX(params)

* **Description**: Draw rectangle with JavaFX in layer.

* **Parameter**:
    * *Object* params - configuration params
        * params.width: horizontal rectangle dimension
        * params.height: vertical rectangle dimension
        * params.offsetX: horizontal offset in layer
        * params.offsetY: vertical offset in layer
        * params.color: rectangle fill color
        * params.rotation: rotation angle
        * params.shadow.size: shadow size
        * params.shadow.color: shadow color (rgba|hex)
        * params.shadow.offsetX: horizontal shadow offset
        * params.shadow.offsetY: vertical shadow offset
        * params.border.size: size of border stroke
        * params.border.color: color of border stroke
        * params.border.position: position of border stroke (inside|centered|outside)

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.drawShapeFX(shape, style)

* **Description**: Draw any type of JavaFX shape (path, rectangle, text, ...)

* **Parameter**:
    * *Packages.javafx.scene.shape.Path* shape - JavaFX shape
    * *Object* style - configuration params
        * style.offsetX: horizontal offset in layer
        * style.offsetY: vertical offset in layer
        * style.shadow.size: shadow size
        * style.shadow.color: shadow color
        * style.shadow.offsetX: horizontal shadow offset
        * style.shadow.offsetY: vertical shadow offset

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.drawTextFX(params)

* **Description**: Draw JavaFX text on current SlimLayer.

* **Parameter**:
    * *Object* params - configuration params
        * params.text: the text content
        * params.x: horizontal offset
        * params.y: vertical offset
        * params.font.color: text color (hex|rgba)
        * params.font.name: font
        * params.font.size: text size
        * params.font.weight: bold (flag)
        * params.font.italic: italic (flag)
        * params.font.align: left|center|right
        * params.font.valign: top|center|bottom
        * params.rotation: rotation angle
        * params.shadow.size: size of text shadow
        * params.shadow.color: color of text shadow (hex|rgba)
        * params.shadow.xOffset: vertical shadow offset
        * params.shadow.yOffset: horizontal shadow offset
        * params.outline.size: size of text outline
        * params.outline.color: color of text outline (hex|rgba)

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.equals(slimLayer)

* **Description**: Check if slimLayer equals current SlimLayer instance.

* **Parameter**:
    * *cs.obj.SlimLayer* slimLayer - layer to compare with

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.export(path, name)

* **Description**: Export SlimLayer to common image (png/jpeg/...).

* **Parameter**:
    * *string* path - file path for export
    * *string* name - file name for export

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.getAverageColor(format)

* **Description**: Get SlimLayer average color in hex|rgba.

* **Parameter**:
    * *string* format - hex|rgba

* **Return**: *object|string*

### cs.obj.SlimLayer.prototype.getBottom()

* **Description**: Get bottom value in vertical direction.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getChild(index)

* **Description**: Get child SlimLayer of current SlimLayer at index.

* **Parameter**:
    * *integer* index - position index in list of child layers

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.getChildren()

* **Description**: Get child SlimLayers of current SlimLayer.

* **Parameter**: none

* **Return**: *array*

### cs.obj.SlimLayer.prototype.getHeight()

* **Description**: Get layer height.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getHorizontalMiddle()

* **Description**: Get the horizontal middle as integer.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getIndex()

* **Description**: Get index of current SlimLayer instance in SmallLayeredImage.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getImage()

* **Description**: Get the layer as java buffered image.

* **Parameter**: none

* **Return**: *Packages.java.awt.image.BufferedImage*

### cs.obj.SlimLayer.prototype.getLeft()

* **Description**: Get left value in horizontal direction.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getName()

* **Description**: Get the layer name.

* **Parameter**: none

* **Return**: *string*

### cs.obj.SlimLayer.prototype.getRawSlimLayer()

* **Description**: Get raw SlimLayer instance.

* **Parameter**: none

* **Return**: *Packages.de.projektmotor.slim.viewer.image.SlimLayer*

### cs.obj.SlimLayer.prototype.getRight()

* **Description**: Get right value in horizontal direction.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getTop()

* **Description**: Get top value in vertical direction.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getType()

* **Description**: Get layer type as text.

* **Parameter**: none

* **Return**: *string*

### cs.obj.SlimLayer.prototype.getVerticalMiddle()

* **Description**: Get the vertical middle as integer.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.getWidth()

* **Description**: Get layer width.

* **Parameter**: none

* **Return**: *integer*

### cs.obj.SlimLayer.prototype.setBackgroundColor(red, green, blue, alpha)

* **Description**: Get layer width.

* **Parameter**:
    * *integer* red: 0...255
    * *integer* green: 0...255
    * *integer* blue: 0...255
    * *integer* alpha: 0...255

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.setBounds(x, y, width, height)

* **Description**: Get layer width.

* **Parameter**:
    * *integer* x: vertical offset 
    * *integer* y: horizontal offset
    * *integer* width: horizontal size
    * *integer* height:  vertical size

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.setParent(slimLayer)

* **Description**: Set the parent SlimLayer of current SlimLayer instance.

* **Parameter**:
    * *cs.obj.SlimLayer* slimLayer: layer to set as new parent

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.setSmallLayeredImage(slimLayer)

* **Description**: Set superior SmallLayeredImage.

* **Parameter**:
    * *cs.obj.SmallLayeredImage* smallLayeredImage: slimage to set

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.setX(offsetX)

* **Description**: Set horizontal postion of layer in image.

* **Parameter**:
    * *integer* offsetX: horizontal offset

* **Return**: *cs.obj.SlimLayer*

### cs.obj.SlimLayer.prototype.setY(offsetY)

* **Description**: Set vertical postion of layer in image.

* **Parameter**:
    * *integer* offsetY: vertical offset

* **Return**: *cs.obj.SlimLayer*
