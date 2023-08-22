---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.14.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Getting Started with Leafmap

```{contents}
:local:
:depth: 2
```

## Introduction

Welcome to the world of geospatial data science! In this chapter, we will introduce the [leafmap](https://leafmap.org) Python package for interactive visualization and analysis of geospatial data. We will demonstrate how to use it to create interactive maps using different mapping backends and change basemaps interactively. We will also show you how to use leafmap with various cloud-computing platforms, including Google Colab, Amazon SageMaker Studio Lab, and Microsoft Planetary Computer.

## Geospatial data science

## Introducing leafmap

## Key features

## Installation

### Installing with conda

```bash
conda create -n geo python
conda activate geo
conda install -c conda-forge mamba
mamba install -c conda-forge leafmap
```

```bash
mamba install -c conda-forge pygis
```

### Installing with pip

```bash
pip install leafmap
```

### Installing from source

```bash
git clone https://github.com/opengeos/leafmap
cd leafmap
pip install .
```

```bash
pip install git+https://github.com/opengeos/leafmap
```

### Upgrading leafmap

```bash
pip install -U leafmap
```

```bash
conda update -c conda-forge leafmap
```

```{code-cell} ipython3
import leafmap
leafmap.update_package()
```

### Using Docker

```bash
docker run -it -p 8888:8888 giswqs/leafmap:latest
```

## JupyterLab

```bash
conda activate geo
```

```bash
jupyter lab
```

```{code-cell} ipython3
import leafmap

m = leafmap.Map()
m
```

## Google Colab

```{code-cell} ipython3
%pip install leafmap
```

```{code-cell} ipython3
import leafmap

m = leafmap.Map()
m
```

## Amazon SageMaker Studio Lab

```bash
!conda install -c conda-forge leafmap -y
```

```{code-cell} ipython3
import leafmap

m = leafmap.Map()
m
```

## Microsoft Planetary Computer

```bash
!mamba update -c conda-forge leafmap -y
```

```{code-cell} ipython3
import leafmap

m = leafmap.Map()
m
```

## Mapping backends

```bash
mamba install -c conda-forge pygis
```

### Ipyleaflet

```{code-cell} ipython3
import leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[37.75, -122.43], zoom=12, height='550px')
m
```

```{code-cell} ipython3
m = leafmap.Map(toolbar_control=False, draw_control=False)
m
```

```{code-cell} ipython3
m.clear_controls()
m
```

```{code-cell} ipython3
m.to_html("map.html", title="My Map", width="100%", height="800px")
```

### Folium

```{code-cell} ipython3
import leafmap.foliumap as leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[37.75, -122.43], zoom=12, height='500px')
m
```

```{code-cell} ipython3
m.to_html('folium.html')
```

### Bokeh

```{code-cell} ipython3
import leafmap.bokehmap as leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4, height=400)
m
```

### Plotly

```{code-cell} ipython3
import leafmap.plotlymap as leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[20, 0], zoom=1, height=400)
m
```

```{code-cell} ipython3
# leafmap.fix_widget_error()
```

### Pydeck

```{code-cell} ipython3
import leafmap.deck as leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[20, 0], zoom=1)
m
```

### KeplerGL

```{code-cell} ipython3
import leafmap.kepler as leafmap
```

```{code-cell} ipython3
m = leafmap.Map(center=[20, 0], zoom=1)
m
```

## Adding basemaps

### Built-in basemaps

```{code-cell} ipython3
import leafmap
```

```{code-cell} ipython3
m = leafmap.Map(basemap='OpenTopoMap')
m
```

```{code-cell} ipython3
m.add_basemap('Stamen.Terrain')
```

```{code-cell} ipython3
for basemap in leafmap.basemaps.keys():
    print(basemap)
```

```{code-cell} ipython3
len(leafmap.basemaps)
```

### XYZ tiles

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_tile_layer(
    url="https://a.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png",
    name="OpenStreetMap.HOT",
    attribution="OpenStreetMap",
)
m
```

### WMS tiles

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4, height='500px')
url = 'https://imagery.nationalmap.gov/arcgis/services/USGSNAIPPlus/ImageServer/WMSServer?'
m.add_wms_layer(
    url=url,
    layers='USGSNAIPPlus:NaturalColor',
    name='NAIP',
    format='image/png',
    attribution='USGS',
    transparent=True,
)
m
```

## Summary

