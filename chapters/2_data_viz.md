---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
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

## Technical requirements

## Visualizing vector data

### GeoJSON

#### Point data

```{code-cell} ipython3import leafmap
```

```{code-cell} ipython3cities = 'https://open.gishub.org/data/world/world_cities.geojson'
```

```{code-cell} ipython3m = leafmap.Map()
```

```{code-cell} ipython3m.add_geojson(cities, layer_name='Cities')
m
```

```{code-cell} ipython3m = leafmap.Map()
m.add_marker_cluster(cities, layer_name='Cities')
m
```

#### Line data

```{code-cell} ipython3url = 'https://open.gishub.org/data/vector/cables.geojson'
```

```{code-cell} ipython3m = leafmap.Map(center=[0, 0], zoom=2)
m.add_geojson(url, layer_name="Submarine Cables", zoom_to_layer=False)
m
```

```{code-cell} ipython3m = leafmap.Map(center=[0, 0], zoom=2)
m.add_basemap("CartoDB.DarkMatter")
callback = lambda feat: {"color": feat["properties"]["color"], "weight": 1}
m.add_geojson(url, layer_name="Cable lines", style_callback=callback)
m
```

#### Polygon data

```{code-cell} ipython3url = "https://open.gishub.org/data/world/countries.geojson"
```

```{code-cell} ipython3m = leafmap.Map(center=[0, 0], zoom=2)
m.add_geojson(url, layer_name="Countries")
m
```

```{code-cell} ipython3m = leafmap.Map(center=[0, 0], zoom=2)
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
m.add_geojson(url, layer_name="Countries", style=style, hover_style=hover_style)
m
```

### Shapefile

```{code-cell} ipython3url = "https://open.gishub.org/data/us/us_states.zip"
```

```{code-cell} ipython3m = leafmap.Map(center=[40, -100], zoom=4)
m.add_shp(url, layer_name="US States")
m
```

### GeoDataFrame

```{code-cell} ipython3import leafmap
import geopandas as gpd
```

```{code-cell} ipython3gdf = gpd.read_file(url)
gdf.head()
```

```{code-cell} ipython3m = leafmap.Map(center=[40, -100], zoom=4)
m.add_gdf(gdf, layer_name="US States")
m
```

### GeoPackage

```{code-cell} ipython3url = "https://open.gishub.org/data/us/us_regions.gpkg"
```

```{code-cell} ipython3m = leafmap.Map(center=[40, -100], zoom=4)
m.add_vector(url, layer_name="US Regions")
m
```

### Vector tile layer

```{code-cell} ipython3url = 'https://tile.nextzen.org/tilezen/vector/v1/512/all/{z}/{x}/{y}.mvt?api_key=gCZXZglvRQa6sB2z7JzL1w'
attribution = "Nextzen"
```

```{code-cell} ipython3m = leafmap.Map()
m.add_vector_tile_layer(url, attribution)
m
```

## Visualizing raster data

```{code-cell} ipython3
```

### GeoTIFF

```{code-cell} ipython3
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
