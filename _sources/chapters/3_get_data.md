---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Getting Geospatial Data

```{contents}
:local:
:depth: 2
```

## Introduction

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

- [Open 3_get_data.ipynb in Google Colab](https://colab.research.google.com/github/giswqs/leafmap-book/blob/master/chapters/3_get_data.ipynb)
- [Open 3_get_data.ipynb in Amazon SageMaker Studio Lab](https://studiolab.sagemaker.aws/import/github/giswqs/leafmap-book/blob/master/chapters/3_get_data.ipynb)
- [Open 3_get_data.ipynb in Microsoft Planetary Computer](https://pccompute.westeurope.cloudapp.azure.com/compute/hub/user-redirect/git-pull?repo=https://github.com/giswqs/leafmap-book&urlpath=lab/tree/leafmap-book/chapters/3_get_data.ipynb&branch=master)

Once in the selected cloud environment, you can uncomment the following line and run the cell to install pygis, which includes leafmap and all the necessary dependencies:

```{code-cell} ipython3
# %pip install pygis
```

The installation process may take 2-3 minutes. Once pygis has been installed successfully, restart the kernel to enable the newly installed packages.

To begin, import the necessary libraries that will be used in this chapter:

```{code-cell} ipython3
import leafmap
```

## Basemaps

## Census data

## The National Map

## OpenStreetMap

## OpenAerialMap

## Creating vector data

## Editing vector data

## Creating raster data

### From GeoTIFF

### From NumPy array

## Planetary Computer

## AWS Open Data

## Custom STAC catalog

## Summary

## References

- https://leafmap.org/notebooks/15_openstreetmap
- https://leafmap.org/notebooks/18_point_layer
- https://leafmap.org/notebooks/30_census_data
- https://leafmap.org/notebooks/31_search_basemaps
- https://leafmap.org/notebooks/37_planetary_computer
- https://leafmap.org/notebooks/42_create_cog
- https://leafmap.org/notebooks/45_create_vector
- https://leafmap.org/notebooks/46_edit_vector
- https://leafmap.org/notebooks/47_numpy_to_cog
- https://leafmap.org/notebooks/56_download_ned
- https://leafmap.org/notebooks/57_national_map
- https://leafmap.org/notebooks/64_stac_search
- https://leafmap.org/notebooks/68_openaerialmap
- https://leafmap.org/notebooks/69_turkey_earthquake
- https://leafmap.org/notebooks/71_aws_s3
- https://leafmap.org/notebooks/73_custom_stac
- https://leafmap.org/notebooks/74_tms_to_geotiff
- https://leafmap.org/notebooks/78_read_raster
