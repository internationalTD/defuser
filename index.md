# Defuser

current release: `v0.0.1-alpha`
<br/>
release date: `22.10.2022`
<br/>
A Plugin for Photoshop and Krita that can interface with [this Stable Diffusion WebUI host](https://github.com/AUTOMATIC1111/stable-diffusion-webui). 
<br/>You won't need to switch to another WebUI or modify the repository in any way.

## Features
* text to image
* image to image
* inpainting
* outpainting
* inside Photoshop and Krita, so:
    * __NO__ fussing around with the inpainter tool in the browser / uploading masks
    * __NO__ copying and pasting from and to WebUI
    * __NO__ context switching just because you needed a new batch of images

#### Planned features:
* upscaling
* further workflow improvements
* standalone face fix
* pause and interrupt
* "render queue"
* experiments

## Installation

#### Krita
1. Copy this url to your clipboard: `REPLACEME`
2. With Krita open, go to `Tools - Scripts - Import Python Plugin from Web` and paste the link
3. Hit yes to activate, then restart Krita
4. Open the docker from `Settings - Dockers - Defuser` and start proomting!

* alternatively, you can also download the release and install via Import Python Plugin from file

#### Photoshop
1. Download the latest release: `REPLACEME`
2. Open the file. Creative Cloud should pop up and prompt you to install. If it hangs/freezes before that, just double-click the file again, this is an Adobe CC bug.
3. Open the Docker under `Plugins - Defuser` and start proomting!

### Quick Test
To test the installation, we are going to create any size document, then an exactly 512x512 selection, and finally generate a txt2img output. Here is how to do that:

1. Create a new document.
2. Press the "Generate" button and follow instructions, if any.
# Usage

### Start the WebUI with webui_user.bat as usual and just open Krita or Photoshop to generate.
The plugin will take care of requirements automatically for you. For example, it might create selections and inpainting masks and it will switch to an appropriate tool.

### txt2img:
Defuser will never stretch or crop generated images. This means that if you press generate when no selection is made, Defuser defaults to a 512x512 selection. If you want a different aspect ratio, make a rough selection and press generate to snap to the nearest increment quickly. You don't need to waste time trying to be pixel-perfect yourself.

### img2img:
If you want to transfer from, say, a pencil sketch to watercolor, you should run
img2img "stacked". Don't try to achieve a perfect result in one run. When you get your result, use that as input. Decrease noise_scale with subsequent generations, or the output will change too much.

### Inpainting:
After generation, the current mask is hidden. if you want to reuse it, you can unhide the `!sdmask` layer.
Experiment with different brush hardnesses and `mask_blur` settings. If your result is a blurry mess, you can change the `masked_content` parameter.

### Outpainting:
If your input image borders the canvas edge, your result might look cropped. If you move the resulting layer, or the canvas, the result will be in frame. This behavior will be improved in a future release.

### Additional Tips:

3. Generation settings are saved in the layers, press __any button marked ♻️__ to copy the settings from the selected layer into your docker. This works for any tab, regardless of what tab you used to generate. The button at the top copies __all settings__, _seed included_!
