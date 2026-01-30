---
description: Create TRMNL-friendly images.
---

# ImageMagick Guide

TRMNL supports BMP3 and PNG images natively, starting with [FW v1.5.2](https://github.com/usetrmnl/firmware/releases/tag/v1.5.2). Below are some tips to generate TRMNL compatible images for DIY devices or [Alias](https://help.trmnl.com/en/articles/10701448-alias-plugin)/[Redirect](https://help.trmnl.com/en/articles/11035846-redirect-plugin) plugin applications.

## Generating a BMP3 image <a href="#h_de4d75d195" id="h_de4d75d195"></a>

Convert command

```
magick input.png -monochrome -colors 2 -depth 1 -strip bmp3:output.bmp
```

Identify command

```
% magick identify output.bmp 
output.bmp BMP3 800x480 800x480+0+0 1-bit sRGB 2c 48062B 0.020u 0:00.001
```

Please note that the output of above needs to match exactly with your file.

## Generating a PNG image (1 bit) <a href="#h_6b95d41fbd" id="h_6b95d41fbd"></a>

Converting an image

```
magick input.png -monochrome -colors 2 -depth 1 -strip png:output.png    
```

Dithering an image

```
magick input.png -dither FloydSteinberg -remap pattern:gray50 -depth 1 -strip png:output.png
```

Identify command

```
% magick identify output.png 
output.png PNG 800x480 800x480+0+0 8-bit Grayscale Gray 2c 1607B 0.000u 0:00.000
```

## Generating a PNG image (2 bit) <a href="#h_6b95d41fbd" id="h_6b95d41fbd"></a>

**This feature is experimental** and designed for OG model devices running [FW 1.6.0+](https://trmnl.com/flash) with grayscale + fast refresh support. After creating an image, upload it to a public or private/local network and point to it with an [Alias plugin](https://help.trmnl.com/en/articles/10701448-alias-plugin) instance.

First create a color map:

```
magick -size 4x1 xc:#000000 xc:#555555 xc:#aaaaaa xc:#ffffff +append -type Palette colormap-2bit.png
```

Then convert your image with the map:

```
magick input.jpeg -resize 800x480\! -dither FloydSteinberg -remap colormap-2bit.png -define png:bit-depth=2 -define png:color-type=0 output.png
```
