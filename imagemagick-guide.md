# ImageMagick Guide

TRMNL supports BMP3 and PNG images natively, starting with [FW v1.5.2](https://github.com/usetrmnl/firmware/releases/tag/v1.5.2). Below are some tips to generate TRMNL compatible images for DIY devices or [Alias](https://help.usetrmnl.com/en/articles/10701448-alias-plugin)/[Redirect](https://help.usetrmnl.com/en/articles/11035846-redirect-plugin) plugin applications.

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

