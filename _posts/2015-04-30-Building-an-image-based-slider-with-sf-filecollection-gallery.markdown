---
layout: post
title:  "Building a slider with sf-filecollection-gallery"
date:   2015-04-28 12:52:19
tags: typo3 cms sf-filecollection-gallery slider
---
# sf_filecollection_gallery
Our extension [sf_filecollection_gallery][github-link] was published to the [typo3 repository][t3-repo-link] a while ago and got some bugfix- and feature-updates already.
As a next step i want to introduce an easy way to implement a slider, based on this extension. There may be ways to implement an image slider with the TYPO3 Image content element,
but the biggest advantage is, you are able to use the FileCollection, either folder based or file based, to define the content of the slider.

## BxSlider
For this example i am using bxslider as slider library. You are able to differ the template, to fit the markup you need.

### Implement the slider
First you need to download the files of [bxSlider][bx-slider]. After you uploaded the necessary files you may include them via TypoScript:
<script src="https://gist.github.com/machwatt/ca0256f885c0a983e43b.js"></script>
Furthermore the slider includes some static content like backgrounds. These are located in /images` of your bxSlider download. You should upload/replace them and may adjust the CSS to your needs.

## Install sf_filecollection_gallery
Now that we got the bxSlider files to the frontend, we should install the extension. You get the latest stable version via TYPO3 Extension Manager, but you might wanna have a look at the [development branch][github-develop-link].
After you installed the extension, you need to include the **static template** to your root template.

### Including FileCollection
You may store the FileCollections in a *sys_folder* or somewhere else in your installation. 
After you included the plugin as a content element, it shows you a field to select the FileCollection.
 
## Create the template
As some may already know, its possible to offer own templates for installed extensions. We want to change the default template to fit the bxSlider markup.
TypoScript has an array called *templateRootPaths*, which we made available in [version 1.1][github-1.1.1-link]. 
This way you can easily overwrite the default templates (they have the id *0* in the array), without having to overwrite all templates, because there is fallback functionality given.
All we need to do is to link our template on the next higher identifier:
<script src="https://gist.github.com/machwatt/9f571b4b8a671af6fa5b.js"></script>

Of course we need to make that file path available in fileadmin. So we create a new file **path/to/Templates/Gallery/List.html**:
<script src="https://gist.github.com/machwatt/fd8f2ce545c4f64d7330.js"></script>

That's all we need to do, to get another template for sf_filecollection_gallery.

## Initialising the slider
If you had read carefully until now, you might find some file missing. We included a init.js in our page defining TypoScript.
This way we initialise the slider in the frontend:
<script src="https://gist.github.com/machwatt/e5a76ef43afccc898958.js"></script>
If you need some options for the slider, a full list can be found [here][bx-slider-options].


# Conclusion and Feedback
As you see, its not that hard to change the layout and use our extension your very own way.
There may be other use cases for sf_filecollection_gallery, maybe not even as a gallery or slider.

If you have feedback/isses feel free to [commit them][github-issues]. 
I would be glad, to hear from you and maybe see some other implementations of this useful extension.




[github-link]:      https://github.com/Skyfillers/sf_filecollection_gallery
[github-develop-link]:      https://github.com/Skyfillers/sf_filecollection_gallery/tree/develop
[github-1.1.1-link]:      https://github.com/Skyfillers/sf_filecollection_gallery/releases/tag/v1.1.1
[t3-repo-link]:     http://typo3.org/extensions/repository/view/sf_filecollection_gallery
[bx-slider]:		http://bxslider.com
[bx-slider-options]:		http://bxslider.com/options
[github-issues]:		https://github.com/Skyfillers/sf_filecollection_gallery/issues