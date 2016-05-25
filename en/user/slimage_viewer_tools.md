# The SlimageViewer

To speed up your templating process, CTRL+SPACE comes with a component called SlimageViewer. It allows you opening Photoshop
files directly inside CTRL+SPACE.

Stop. This not really the truth. The Photoshop file format is quite complex and not very suitable for use in external
tools. The SlimageViewer component does not deal with Photoshop files directly, instead it uses its own file format called
**CSImage**. This one is optimized for use in CTRL+SPACE and for the retrieval of layer 
informations.

* [Photoshop to Slimage conversion](#Photoshop_to_Slimage_conversion)
* [Using the SlimageViewer](#Using_the_SlimageViewer)
    * [Single and Multi Selection Mode](#Single_and_Multi_Selection_Mode)
    * [Layer Merge](#Layer_Merge)
    * [Snapshots](#Snapshots)
    * [Show / Hide Layers](#Show_Hide_Layers)
    * [Text Layer Splicing](#Text_Layer_Splicing)
    * [Layer Lightbox](#Layer_Lightbox)

## Photoshop to Slimage conversion

coming soon!

## Using the SlimageViewer

Basically the SlimageViewer is used to view the graphics template and select layers for use with Blueprints. If your designer
produces its output according to your needs, you may be fine with this core features. But what if you get a Photoshop file which
looks pretty nice, but doesn`t satisfy your claims? For example you need a specific part of layer as stand alone layer,
or you need a merged layer consisting out of multiple single layers. Therefor the SlimageViewer has several tools which should help
you doing your work.

In the following paragraphs we will explain these tools und show you how to use them.

### Single and Multi Selection Mode

With the **single selection mode** you select layers by a simple click. With pressed `Strg` key, the selection of multiple layers
is also possible.

In **multi selection mode** layer selection is done by dragging a selection rectangle, similar to most of the graphics tools. 
This mode gives you a live preview, where you can see all the currently selected layers.

![SlimageViewer - multi selection mode](/images/simlageviewer_multi_selection_mode.png)

### Layer Merge

This tool merges the currently selected layers into a new one and adds the new layer at the top of the layer tree. Just
click the layer merge button and enter a name.

![SlimageViewer - merge button](/images/simlageviewer_layer_merge_button.png)
![SlimageViewer - enter name](/images/simlageviewer_layer_merge_name.png)

### Snapshots

coming soon!

### Show / Hide Layers

Showing and hiding of layers could be done in two different ways. The SlimageViewer is one possibility. You first have to 
select the layers and press the `hide` button afterwards.

![SlimageViewer - hide layer](/images/simlageviewer_layer_hide.png)

A second possibility to show or hide layers is the Navigator window. Therefor just open the context menu with a right click and
select `toggle layer visibility`.

### Text Layer Splicing

This tool allows you to split up one large text layer into multiple small ones. First the input text layer has to be selected.
Afterwards click on the text layer splicing button. A border around the input text layer with buttons at every side and a 
textarea (including the complete text) occurs. 

![SlimageViewer - text layer splicing textarea](/images/simlageviewer_text_layer_splicing_textarea.png)

To create a new text layer for a smaller text part, select the text you want to extract, drag the borders around
the selected text part and klick the button on the right. A new text layer is places on top of the layer tree.

![SlimageViewer - text layer splicing](/images/simlageviewer_text_layer_splicing_splice.png)

### Layer Lightbox

coming soon!