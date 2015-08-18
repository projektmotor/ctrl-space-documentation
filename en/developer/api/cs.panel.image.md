# API cs.panel.image

### cs.panel.image.clear()

* **Description**: Clears all the painted stuff in image panel.

* **Parameter**: none

* **Return**: null

### cs.panel.image.close(smallLayeredImage)

* **Description**: Close SlimageViewer for SmallLayeredImage.

* **Parameter**:
    * *cs.obj.SmallLayeredImage* smallLayeredImage: slimage to close

* **Return**: null

### cs.panel.image.drawCircle(center, radius, color)

* **Description**: Draw circle into active SlimageViewer.

* **Parameter**:
    * *object* center: object with `x` & `y` property
    * *integer* radius: radius in px
    * *object|string* color: circle color

* **Return**: null

### cs.panel.image.drawLine(x1, y1, x2, y2, label, color)

* **Description**: Draw line into active SlimageViewer.

* **Parameter**:
    * *integer* x1: horizontal start
    * *integer* y1: vertical start
    * *integer* x2: horizontal end
    * *integer* y2: vertical end
    * *string* label: line label
    * *string* color: line color

* **Return**: null

### cs.panel.image.drawRectangle(x, y, width, height)

* **Description**: Draw rectangle into active SlimageViewer.

* **Parameter**:
    * *integer* x: horizontal offset
    * *integer* y: vertical offset
    * *integer* width: horizontal length
    * *integer* height: vertical length

* **Return**: null

### cs.panel.image.drawText(x, y, text, color)

* **Description**: Draw text into active SlimageViewer.

* **Parameter**:
    * *integer* x: horizontal offset
    * *integer* y: vertical offset
    * *string* text: text content
    * *object|string* color: text color as hex string or rgba object

* **Return**: null

### cs.panel.image.getActiveSlimage()

* **Description**: Get the currently active slimage model object (SmallLayeredImage).

* **Parameter**: none

* **Return**: *cs.obj.SmallLayereImage*

### cs.panel.image.open(smallLayeredImage)

* **Description**: Opens a SmallLayeredImage in SlimageViewer.

* **Parameter**:
    * *cs.obj.SmallLayereImage* smallLayeredImage: slimage to open in editor

* **Return**: null

### cs.panel.image.setActiveSlimage(smallLayeredImage)

* **Description**: Set the currently active SmallLayeredImage.

* **Parameter**:
    * *cs.obj.SmallLayereImage* smallLayeredImage: slimage to set active

* **Return**: null