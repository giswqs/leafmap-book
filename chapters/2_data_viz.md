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

# Basic Map Visualization

```{contents}
:local:
:depth: 2
```

## Introduction

Map visualization is a powerful tool for analyzing and communicating spatial data. In this chapter, we will explore various techniques for visualizing vector data on a map. We will cover different file formats and demonstrate how to use them to create interactive and informative maps. By the end of this chapter, you will have a solid understanding of basic map visualization techniques and be able to apply them to your own projects.

## Technical requirements

```{code-cell} ipython3
import leafmap
```

## Visualizing vector data

### GeoJSON

#### Point data

```{code-cell} ipython3
cities = 'https://open.gishub.org/data/us/cities.geojson'
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
```

```{code-cell} ipython3
m.add_geojson(cities, layer_name='Cities')
m
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_marker_cluster(cities, layer_name='Cities')
m
```

#### Line data

```{code-cell} ipython3
cables = 'https://open.gishub.org/data/vector/cables.geojson'
```

```{code-cell} ipython3
m = leafmap.Map(center=[0, 0], zoom=2)
m.add_geojson(cables, layer_name="Submarine Cables", zoom_to_layer=False)
m
```

```{code-cell} ipython3
m = leafmap.Map(center=[0, 0], zoom=2)
m.add_basemap("CartoDB.DarkMatter")
callback = lambda feat: {"color": feat["properties"]["color"], "weight": 1}
m.add_geojson(cables, layer_name="Cable lines", style_callback=callback)
m
```

#### Polygon data

```{code-cell} ipython3
countries = "https://open.gishub.org/data/world/countries.geojson"
```

```{code-cell} ipython3
m = leafmap.Map(center=[0, 0], zoom=2)
m.add_geojson(countries, layer_name="Countries")
m
```

```{code-cell} ipython3
m = leafmap.Map(center=[0, 0], zoom=2)
style = {
    "stroke": True,
    "color": "#0000ff",
    "weight": 2,
    "opacity": 1,
    "fill": True,
    "fillColor": "#0000ff",
    "fillOpacity": 0.1,
}
hover_style = {"fillOpacity": 0.7}
m.add_geojson(countries, layer_name="Countries", style=style, hover_style=hover_style)
m
```

### Shapefile

```{code-cell} ipython3
states = "https://open.gishub.org/data/us/us_states.zip"
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_shp(states, layer_name="US States")
m
```

### GeoDataFrame

```{code-cell} ipython3
import geopandas as gpd
```

```{code-cell} ipython3
gdf = gpd.read_file(states)
gdf.head()
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_gdf(gdf, layer_name="US States")
m
```

### GeoPackage

```{code-cell} ipython3
regions = "https://open.gishub.org/data/us/us_regions.gpkg"
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_vector(regions, layer_name="US Regions")
m
```

### Vector tile layer

```{code-cell} ipython3
m = leafmap.Map()
url = "https://planetarycomputer.microsoft.com/api/data/v1/vector/collections/ms-buildings/tilesets/global-footprints/tiles/{z}/{x}/{y}"
attribution = "Microsoft"
vector_tile_layer_styles = {}
m.add_vector_tile_layer(url, attribution, vector_tile_layer_styles)
m
```

## Visualizing raster data

```{code-cell} ipython3

```

### GeoTIFF

```{code-cell} ipython3
dem = 'dem.tif'
landsat = 'landsat.tif'
```

```{code-cell} ipython3
dem_url = 'https://open.gishub.org/data/raster/dem.tif'
landsat_url = 'https://open.gishub.org/data/raster/landsat7.tif'
```

### COG

```{code-cell} ipython3

```

### STAC

```{code-cell} ipython3

```

## Legends

```{code-cell} ipython3

```

## Colorbars

```{code-cell} ipython3

```

## Labels

```{code-cell} ipython3

```

## Split maps

```{code-cell} ipython3

```

## Linked maps

```{code-cell} ipython3

```

## Summary

```{code-cell} ipython3

```

## References

- https://leafmap.org/notebooks/03_cog_stac
- https://leafmap.org/notebooks/05_load_raster
- https://leafmap.org/notebooks/10_add_vector
- https://leafmap.org/notebooks/06_legend
- https://leafmap.org/notebooks/07_colorbar
- https://leafmap.org/notebooks/11_linked_maps
- https://leafmap.org/notebooks/12_split_map
- https://leafmap.org/notebooks/23_colormaps
- https://leafmap.org/notebooks/36_add_labels
- https://leafmap.org/notebooks/59_create_legend
- https://leafmap.org/notebooks/19_map_to_html
- https://leafmap.org/notebooks/17_vector_tile_layer
