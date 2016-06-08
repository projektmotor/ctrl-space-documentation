# API cs.panel.image

### cs.panel.image.clear()

* **Description**: Clears all the painted stuff in image panel.

* **Parameter**: none

* **Return**: null

### cs.panel.image.close(smallLayeredImage)

* **Description**: Close CSImageViewer for SmallLayeredImage.

* **Parameter**:
    * *cs.obj.SmallLayeredImage* smallLayeredImage: CSImage to close

* **Return**: null

### cs.panel.image.drawCircle(center, radius, color)

* **Description**: Draw circle into active CSImageViewer.

* **Parameter**:
    * *object* center: object with `x` & `y` property
    * *integer* radius: radius in px
    * *object|string* color: circle color

* **Return**: null

### cs.panel.image.drawLine(x1, y1, x2, y2, label, color)

* **Description**: Draw line into active CSImageViewer.

* **Parameter**:
    * *integer* x1: horizontal start
    * *integer* y1: vertical start
    * *integer* x2: horizontal end
    * *integer* y2: vertical end
    * *string* label: line label
    * *string* color: line color

* **Return**: null

### cs.panel.image.drawRectangle(x, y, width, height)

* **Description**: Draw rectangle into active CSImageViewer.

* **Parameter**:
    * *integer* x: horizontal offset
    * *integer* y: vertical offset
    * *integer* width: horizontal length
    * *integer* height: vertical length

* **Return**: null

### cs.panel.image.drawText(x, y, text, color)

* **Description**: Draw text into active CSImageViewer.

* **Parameter**:
    * *integer* x: horizontal offset
    * *integer* y: vertical offset
    * *string* text: text content
    * *object|string* color: text color as hex string or rgba object

* **Return**: null

### cs.panel.image.getActiveCSImage()

* **Description**: Get the currently active CSImage model object (SmallLayeredImage).

* **Parameter**: none

* **Return**: *cs.obj.SmallLayereImage*

### cs.panel.image.open(smallLayeredImage)

* **Description**: Opens a SmallLayeredImage in CSImageViewer.

* **Parameter**:
    * *cs.obj.SmallLayereImage* smallLayeredImage: CSImage to open in editor

* **Return**: null

### cs.panel.image.setActiveCSImage(smallLayeredImage)

* **Description**: Set the currently active SmallLayeredImage.

* **Parameter**:
    * *cs.obj.SmallLayereImage* smallLayeredImage: CSImage to set active

* **Return**: null