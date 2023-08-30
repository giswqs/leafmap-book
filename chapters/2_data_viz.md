---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.15.0
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Visualizing Geospatial Data

```{contents}
:local:
:depth: 2
```

## Introduction

Effective geospatial data visualization is the cornerstone of understanding the world around us. This chapter delves into the realm of visualizing geospatial data using the leafmap library. We will explore various techniques to display vector and raster data, create legends and colorbars to customize the visual appearance of maps, and leverage interactive features for enhanced exploration and analysis.

## Technical requirements

To follow along with this chapter, you will need to have leafmap and several optional dependencies installed. If you have already followed {numref}`ch1:install` - _Installing leafmap_, then you should already have a conda environment with all the necessary packages installed. Otherwise, you can create a new conda environment and install [pygis](https://pygis.gishub.org) with the following commands, which will automatically install leafmap and all the required dependencies:

```bash
conda create -n geo python
conda activate geo
conda install -c conda-forge mamba
mamba install -c conda-forge pygis
```

Next, launch JupyterLab by typing the following commands in your terminal or Anaconda prompt:

```bash
jupyter lab
```

Alternatively, you can use leafmap in a cloud environment without installing anything on your local computer. Click on one of the following links to launch a cloud-based JupyterLab server:

- [Open 2_data_viz.ipynb in Google Colab](https://colab.research.google.com/github/giswqs/leafmap-book/blob/master/chapters/2_data_viz.ipynb)
- [Open 2_data_viz.ipynb in Amazon SageMaker Studio Lab](https://studiolab.sagemaker.aws/import/github/giswqs/leafmap-book/blob/master/chapters/2_data_viz.ipynb)
- [Open 2_data_viz.ipynb in Microsoft Planetary Computer](https://pccompute.westeurope.cloudapp.azure.com/compute/hub/user-redirect/git-pull?repo=https://github.com/giswqs/leafmap-book&urlpath=lab/tree/leafmap-book/chapters/2_data_viz.ipynb&branch=master)

Once in the selected cloud environment, you can uncomment the following line and run the cell to install pygis, which includes leafmap and all the necessary dependencies:

```{code-cell} ipython3
# %pip install pygis
```

The installation process may take 2-3 minutes. Once pygis has been installed successfully, restart the kernel to enable the newly installed packages.

To begin, import the necessary libraries that will be used in this chapter:

```{code-cell} ipython3
import leafmap
```

## Visualizing vector data

### GeoJSON

#### Point data

```{code-cell} ipython3
cities = 'https://open.gishub.org/data/us/cities.geojson'
m = leafmap.Map(center=[40, -100], zoom=4)
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
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_shp(states, layer_name="US States")
m
```

### GeoDataFrame

```{code-cell} ipython3
import geopandas as gpd
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

### GeoTIFF

#### Single-band Rasters

```{code-cell} ipython3
dem = 'dem.tif'
dem_url = 'https://open.gishub.org/data/raster/srtm90.tif'
leafmap.download_file(url=dem_url, output=dem, overwrite=True)
```

```{code-cell} ipython3
m = leafmap.Map()
m.add_raster(dem, cmap='terrain', layer_name="DEM")
m
```

```{code-cell} ipython3
m.add_raster(dem, cmap='viridis', layer_name="DEM2")
```

#### Multi-band Rasters

```{code-cell} ipython3
landsat = 'landsat.tif'
landsat_url = 'https://open.gishub.org/data/raster/landsat.tif'
leafmap.download_file(url=landsat_url, output=landsat)
```

```{code-cell} ipython3
m.add_raster(landsat, band=[4, 3, 2], vmin=1, vmax=100, layer_name="Landsat")
m
```

### COG

#### Introduction to COG

#### Publicly Available COGs

#### Visualizing COGs

```{code-cell} ipython3
import os
os.environ['TITILER_ENDPOINT'] = 'https://titiler.xyz'
```

```{code-cell} ipython3
url = 'https://opendata.digitalglobe.com/events/california-fire-2020/pre-event/2018-02-16/pine-gulch-fire20/1030010076004E00.tif'
```

```{code-cell} ipython3
leafmap.cog_bounds(url)
```

```{code-cell} ipython3
leafmap.cog_center(url)
```

```{code-cell} ipython3
leafmap.cog_bands(url)
```

```{code-cell} ipython3
leafmap.cog_tile(url)
```

```{code-cell} ipython3
m = leafmap.Map()
m.add_cog_layer(url, name="Fire (pre-event)")
m
```

```{code-cell} ipython3
url2 = 'https://opendata.digitalglobe.com/events/california-fire-2020/post-event/2020-08-14/pine-gulch-fire20/10300100AAC8DD00.tif'
m.add_cog_layer(url2, name="Fire (post-event)")
```

### STAC

#### Why Use STAC

#### Visualizing STAC

```{code-cell} ipython3
m = leafmap.Map()
```

```{code-cell} ipython3
url = 'https://canada-spot-ortho.s3.amazonaws.com/canada_spot_orthoimages/canada_spot5_orthoimages/S5_2007/S5_11055_6057_20070622/S5_11055_6057_20070622.json'
```

```{code-cell} ipython3
leafmap.stac_bounds(url)
```

```{code-cell} ipython3
leafmap.stac_center(url)
```

```{code-cell} ipython3
leafmap.stac_bands(url)
```

```{code-cell} ipython3
leafmap.stac_tile(url, bands=['B3', 'B2', 'B1'])
```

```{code-cell} ipython3
m.add_stac_layer(url, bands=['pan'], name='Panchromatic')
m
```

```{code-cell} ipython3
m.add_stac_layer(url, bands=['B3', 'B2', 'B1'], name='False color')
```

## Legends

### Built-in legends

```{code-cell} ipython3
legends = leafmap.builtin_legends
for legend in legends:
    print(legend)
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_basemap('Esri.WorldImagery')
m.add_basemap('NLCD 2021 CONUS Land Cover')
m.add_legend(builtin_legend='NLCD', title='NLCD Land Cover Type')
m
```

### Custom legends

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4)
m.add_basemap('Esri.WorldImagery')
m.add_basemap('NLCD 2021 CONUS Land Cover')

legend_dict = {
    '11 Open Water': '466b9f',
    '12 Perennial Ice/Snow': 'd1def8',
    '21 Developed, Open Space': 'dec5c5',
    '22 Developed, Low Intensity': 'd99282',
    '23 Developed, Medium Intensity': 'eb0000',
    '24 Developed High Intensity': 'ab0000',
    '31 Barren Land (Rock/Sand/Clay)': 'b3ac9f',
    '41 Deciduous Forest': '68ab5f',
    '42 Evergreen Forest': '1c5f2c',
    '43 Mixed Forest': 'b5c58f',
    '51 Dwarf Scrub': 'af963c',
    '52 Shrub/Scrub': 'ccb879',
    '71 Grassland/Herbaceous': 'dfdfc2',
    '72 Sedge/Herbaceous': 'd1d182',
    '73 Lichens': 'a3cc51',
    '74 Moss': '82ba9e',
    '81 Pasture/Hay': 'dcd939',
    '82 Cultivated Crops': 'ab6c28',
    '90 Woody Wetlands': 'b8d9eb',
    '95 Emergent Herbaceous Wetlands': '6c9fb8',
}

m.add_legend(title="NLCD Land Cover Type", legend_dict=legend_dict)
m
```

## Colorbars

```{code-cell} ipython3
import leafmap.colormaps as cm
```

```{code-cell} ipython3
cm.palettes.dem
```

+++

```{code-cell} ipython3
cm.plot_colormap(colors=cm.palettes.dem, axis_off=True)
```

```{code-cell} ipython3
cm.palettes.ndvi
```

```{code-cell} ipython3
cm.plot_colormap(colors=cm.palettes.ndvi)
```

```{code-cell} ipython3
cm.get_palette('terrain', n_class=8)
```

+++

```{code-cell} ipython3
cm.plot_colormap(colors=cm.get_palette('terrain', n_class=8))
```

```{code-cell} ipython3
cm.plot_colormap(colors=["red", "green", "blue"], label="Temperature", font_size=12)
```

```{code-cell} ipython3
cm.plot_colormap(
    colors=["red", "green", "blue"], discrete=True, label="Temperature", font_size=12
)
```

```{code-cell} ipython3
cm.plot_colormap(
    'terrain',
    label="Elevation",
    width=8.0,
    height=0.4,
    orientation='horizontal',
    vmin=0,
    vmax=1000,
)
```

```{code-cell} ipython3
cm.plot_colormap(
    'terrain',
    label="Elevation",
    width=0.4,
    height=4,
    orientation='vertical',
    vmin=0,
    vmax=1000,
)
```

```{code-cell} ipython3
m = leafmap.Map()
m.add_basemap("OpenTopoMap")
m.add_colormap(
    'terrain',
    label="Elevation",
    width=3.0,
    height=0.25,
    orientation='horizontal',
    vmin=0,
    vmax=4000,
)
m
```

```{code-cell} ipython3
m = leafmap.Map()
m.add_basemap("OpenTopoMap")
m.add_colormap(
    'terrain',
    label="Elevation",
    width=0.3,
    height=3,
    orientation='vertical',
    vmin=0,
    vmax=4000,
)
m
```

```{code-cell} ipython3
cm.plot_colormaps(width=8, height=0.4)
```

## Labels

```{code-cell} ipython3
data = "https://open.gishub.org/data/us/us_states.geojson"
```

```{code-cell} ipython3
m = leafmap.Map(center=[40, -100], zoom=4, layers_control=True)
```

```{code-cell} ipython3
m.add_labels(
    data,
    "id",
    font_size="12pt",
    font_color="blue",
    font_family="arial",
    font_weight="bold",
)
m
```

```{code-cell} ipython3
m.remove_labels()
```

## Split maps

```{code-cell} ipython3
leafmap.split_map(
    left_layer="Esri.WorldTopoMap", right_layer="OpenTopoMap", zoom_control=False
)
```

```{code-cell} ipython3
m = leafmap.Map(center=[36.1, -114.9], zoom=10)
m.split_map(
    left_layer="NLCD 2001 CONUS Land Cover",
    right_layer="NLCD 2021 CONUS Land Cover",
    left_label="2001",
    right_label="2021",
    add_close_button=False,
)
m
```

## Linked maps

```{code-cell} ipython3
layers = ['Stamen.Terrain', 'OpenTopoMap']
leafmap.linked_maps(rows=1, cols=2, height='400px', layers=layers)
```

```{code-cell} ipython3
layers = [str(f"NLCD {year} CONUS Land Cover") for year in [2001, 2006, 2011, 2021]]
labels = [str(f"NLCD {year}") for year in [2001, 2006, 2011, 2021]]
leafmap.linked_maps(
    rows=2,
    cols=2,
    height='300px',
    layers=layers,
    labels=labels,
    center=[36.1, -115.2],
    zoom=9,
)
```

## Summary

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
