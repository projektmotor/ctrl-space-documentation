# Your First Steps with CTRL+SPACE

To explain the core features of CTRL+SPACE, we will walk through a little tutorial. It should cover a very basic
templating workflow, including the creation of project, import of a Photoshop file, using some CSImageViewer tools and hydrate
image data with Blueprints.

* [Create a new Project](#Create_a_new_Project)
* [Import Graphics](#Import_Graphics)
* [Using the CSImageViewer](#Using_the_CSImageViewer)
* [Hydrate Imagedata using Blueprints](#Hydrate_Imagedata_using_Blueprints)

## Create a new Project

When you start working with CTRL+SPACE, create a new Project. To open the
project dialog, go to `File > Create Project`. Next you should chose the type of project you want to create. Currently 
HTML5 projects are available. To keep this tutorial as simple as possible, we will choose a basic `HTML5` project
and click next.

![Create a new Project CTRL+SPACE - chose type of project](/images/first_steps_create_project.png)

Now the project location and name has to be set. At this point we decide where all the project data should be stored. 
In our example we will store the project data under `/home/cs/Workspace` and set the project name to `Ctrl-Space-Tutorial`.
If you would like to import some JavaScript resources (jQuery, Angular, ...) or configure some further project details, 
you can click `next`. If there is no need for this, you can finish the project creating and click `finish`.

![Create a new Project CTRL+SPACE - chose project path](/images/first_steps_create_project_path.png)

## Import Graphics

Coming soon!

If you would like to go deeper, you can go on reading the chapter [The CSImageViewer](/en/user/CSImage_viewer_tools.md)

## Using the CSImageViewer

One of the most important CTRL+SPACE components for templating is the CSImageViewer. You can use it to view the graphics
and select layers you need informations from. Therefor open a CSImage via Project Explorer. Activate the
`layer selection mode` and click on the layer you want to select - just as you would use Photoshop.
 
**NOTE:** If there is no CSImage available, see chapter [Import Graphics](#Import_Graphics).

![Using the ImageViewer - layer selection](/images/first_steps_CSImage_viewer_layer_selection.png)

This is nice, but the real world looks a bit different. Your designer has other requirements to the graphics structure than
you may have. Not every part of the graphic might be available as layer, or some parts consist of multiple layers which you 
may need as one merged layer.

Therefor the CSImageViewer comes with several tools. In this turial we will only have a look at one tool, layer
merging. If you need Information about the other tools available in the CSImageViewer component, you can read the chapter
[The CSImageViewer](/en/user/CSImage_viewer_tools.md).

![Using the ImageViewer - multiple layer selection](/images/first_steps_CSImage_viewer_merge_selection.png)
![Using the ImageViewer - merged layer name](/images/first_steps_CSImage_viewer_merge_layer_name.png)

In our example, the RSS icon consists of two layers. The white circle and the icon itself. Later in this tutorial we want to 
save this RSS icon as image. To achive this, we have to merge the two layers into one single layer, which is than exportet as
a new asset. How does it work? First we have to select both layers by keeping the `CTRL` key pressed during selection - just like in Photoshop. Now we only need 
to press the `Layer Merge` button and give the new layer a name - in this example `rss icon`.

Thats it! Now you are ready to work with this layer, hydrate information about it or save it as new asset. 

## Hydrate Imagedata using Blueprints ##

One of the most important features of CTRL+SPACE is reducing time and trouble you usually spend to
extract graphic data when building a template based on a PSD file. For example by measuring margins and paddings, extracting color codes and exporting images as assets.
This doesn't just take a lot of time, let`s be honest - this sucks!

CTRL+SPACE comes with a default Blueprint library, making the relevant meta data available directly in the css/html code completion - see
[Standard Blueprint Library (SBL)](/en/user/standard_blueprint_library.md).

In the previous chapter we created a new layer called `rss icon`. Now we want to create a image-tag inside a 
HTML file and set the top margin via CSS to indent the icon from the top.

### Create new Image-Tag for RSS-Icon ###

We will create an image tag inside an html file and automatically create a png file from the selected layer.
Now select the `rss icon` layer in the CSImageViewer.
Open the HTML file and set the cursor where you want the image tag to be placed.
Now press ctrl+space, select "image" and hit enter. a dialog pop up, asking you for an alt text. enter it or leave it empty and hit return or click the OK button.
the image simplifier will generate the html image tag with an image url pointing to the automatically created png file in the fault image folder.

### Add margin-top via CSS ###

Now we want to get the margin between the top of the image and the `rss icon` layer.
To achieve this, you have to select the `rss icon` layer in the CSImageViewer again. Open the HTML file your image was placed in and add the
class `sample-image` to the image-tag. Now switch to your CSS file and create the CSS selector`.sample-image`. Open the the code completion
by pressing `ctrl + space`, select the `margin-top` code completion and hit the `return` key.

![Hydrate Imagedata with Blueprints - Add margin-top via CSS](/images/first_steps_blueprint_add_margin.png)

Thats it! The Blueprint inserted a CSS property `margin-top`, including the original distance as it is in the PSD.

```css
.sample-image {
    margin-top: 16px;
}

```