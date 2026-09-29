---
description: Create TRMNL-friendly images.
---

# ImageMagick Guide

TRMNL supports BMP3 and PNG images natively, starting with [FW v1.5.2](https://github.com/usetrmnl/trmnl-firmware/releases/tag/v1.5.2). Below are some tips to generate TRMNL compatible images for DIY devices or [Alias](https://help.trmnl.com/en/articles/10701448-alias-plugin)/[Redirect](https://help.trmnl.com/en/articles/11035846-redirect-plugin) plugin applications. These mirror the ImageMagick commands our own render pipeline runs.

{% hint style="info" %}
Match your image to the device. Every model's width, height, bit depth + palette is listed at [trmnl.com/api/models](https://trmnl.com/api/models) (palette colors at [trmnl.com/api/palettes](https://trmnl.com/api/palettes)). Keep PNGs under the model's `image_size_limit` -- 90,000 bytes for ESP32 boards without PSRAM like TRMNL OG, 750,000 bytes for TRMNL X. Our firmware won't draw anything larger.
{% endhint %}

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

## Generating a PNG image - 1 bit <a href="#h_6b95d41fbd" id="h_6b95d41fbd"></a>

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

## Generating a PNG image - 2 bit <a href="#h_6b95d41fbd" id="h_6b95d41fbd"></a>

Use this for 4-gray devices, like the TRMNL OG (2-bit) model on [FW 1.6.0+](https://trmnl.com/flash) with grayscale + fast refresh support. After creating an image, upload it to a public or private/local network and point to it with an [Alias plugin](https://help.trmnl.com/en/articles/10701448-alias-plugin) instance.

```
magick input.png -colorspace Gray -dither None -posterize 4 -alpha off -depth 2 -define png:compression-level=9 -strip png:output.png
```

Dithering an image

```
magick input.png -colorspace Gray -dither FloydSteinberg -posterize 4 -alpha off -depth 2 -define png:compression-level=9 -strip png:output.png
```

## Generating a PNG image - 4 bit <a href="#h_6b95d41fbd" id="h_6b95d41fbd"></a>

Use this for 16-gray devices, like TRMNL X.

```
magick input.png -colorspace Gray -dither None -posterize 16 -alpha off -depth 4 -define png:compression-level=9 -strip png:output.png
```

Dithering an image

```
magick input.png -colorspace Gray -dither FloydSteinberg -posterize 16 -alpha off -depth 4 -define png:compression-level=9 -strip png:output.png
```

## Generating a PNG image - color

For color panels (B/W/R, B/W/R/Y, 6- + 7-color), map every pixel to the panel's palette. This example uses the 6-color palette (`color-6a`); swap in the hex values for your panel from [trmnl.com/api/palettes](https://trmnl.com/api/palettes).

```
magick input.png \( -size 1x1 xc:#FF0000 xc:#00FF00 xc:#0000FF xc:#FFFF00 xc:#000000 xc:#FFFFFF +append +write mpr:palette +delete \) -dither None -remap mpr:palette -define png:compression-level=9 -strip png:output.png
```

Dithering an image

```
magick input.png -normalize -modulate 110,150 -colorspace RGB \( -size 1x1 xc:#FF0000 xc:#00FF00 xc:#0000FF xc:#FFFF00 xc:#000000 xc:#FFFFFF +append +write mpr:palette +delete \) -dither FloydSteinberg -remap mpr:palette -colorspace sRGB -type Palette -define png:compression-level=9 -strip png:output.png
```
