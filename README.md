# Leaflet.TileLayerColorize
A simple and lightweight Leaflet plugin to apply CSS filters on map tiles.

![alt text](https://github.com/xtk93x/Leaflet.TileLayerColorize/blob/master/samples/sidebyside.png)

## Demo
- [Leaflet.TileLayerColorize Demo](https://xtk93x.github.io/Leaflet.TileLayerColorize/)

# Basic Usage
```js
let map = L.map('map').setView([51.505, -0.09], 14);
    
let colorSettings = [
    'blur:0px',
    'brightness:100%',
    'contrast:100%',
    'grayscale:0%',
    'hue:0deg',
    'opacity:100%',
    'invert:0%',
    'saturate:100%',
    'sepia:0%',
]

L.tileLayerColorize('https://maps.wikimedia.org/osm-intl/{z}/{x}/{y}.png', {
    attribution: '<a href="https://wikimediafoundation.org/wiki/Maps_Terms_of_Use">Wikimedia</a>',
    colorize: colorSettings
}).addTo(map);
```
    
# Reference

#### L.tileLayerColorize(url, options)

The only difference between L.tileLayerColorize and the original L.tileLayer is the new option `colorize` inside `options` parameter. 

`colorize` accepts an array of string filters with the following format:

| Filter | Aliases | Description | Example | Default |
| --- | --- | --- | --- | --- |
| **Blur** | blur | Applies a Gaussian blur filtering measured in pixels |  `['blur:2px']` | 0px |
| **Brightness** | brightness or bright | Controls the brightness of tile image |  `['brightness:150%']` | 100% |
| **Contrast** | contrast | Changes the color contrast of tiles |   `['contrast:150%']` | 100% |
| **Grayscale** | grayscale or gray | Changes the color of tiles to a grayscale |  `['grayscale:100%']` | 0% |
| **Hue-Rotate** | hue, hue-rotate or hue-rotation | Applies a hue rotation in degrees on tile colors | `['hue:180deg']` | 0deg |
| **Opacity** | opacity | Defines the opacity of the tiles | `['opacity:60%']` | 100% |
| **Invert** | invert or inv | Invert the tile colors | `['invert:100%']` | 0% |
| **Saturate** | saturate or saturation | Saturates the tile colors | `['saturate:150%']` | 100% |
| **Sepia** | sepia | Converts the tile colors to sepia | `['sepia:0%']` | 0% |
 
# Useful Tips
**The following settings is enough to make most of the light maps to become dark:**

```js
let colorSettings = [
     'grayscale:100%',
     'invert:100%',
]
```
![alt text](https://github.com/xtk93x/Leaflet.TileLayerColorize/blob/master/samples/dark.png)

**To keep water and street colors, a hue rotation around 180deg is very helpful to correct the color inversion:**

```js
let colorSettings = [
     'hue:180deg',
     'invert:100%',
]
```
![alt text](https://github.com/xtk93x/Leaflet.TileLayerColorize/blob/master/samples/dark-colorized.png)
    
**Light maps may also look good:**

```js
let colorSettings = [
     'brightness:110%',
     'hue:90deg',
     'saturate:120%',
]
```
![alt text](https://github.com/xtk93x/Leaflet.TileLayerColorize/blob/master/samples/colorized.png)

**The filter order matters:**

```js
let leftcolorSettings = [
    'invert:100%',
    'brightness:115%',
    'hue:186deg'
]
let rightcolorSettings = [
    'hue:186deg',
    'brightness:115%',
    'invert:100%',
]
```
![alt text](https://github.com/xtk93x/Leaflet.TileLayerColorize/blob/master/samples/filterorder.png)

# Changelog

## 2018.09.23
- Changed from object to array of strings, because the filter order matters. Moreover, the same filter can be used more than once.

## 2018.09.20
- Plugin created
