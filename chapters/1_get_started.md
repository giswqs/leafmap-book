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

# Getting Started with Leafmap

## Introduction

Welcome to the world of geospatial data science! In this chapter, we will introduce the [leafmap](https://leafmap.org) Python package for interactive geospatial data visualization and analysis. We will demonstrate how to use it to create interactive maps using different mapping backends and change basemaps interactively. We will also show you how to use leafmap with various cloud-computing platforms, including Google Colab, Amazon SageMaker Studio Lab, and Microsoft Planetary Computer.

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

## Summary

## References

- https://leafmap.org/notebooks/01_leafmap_intro
- https://leafmap.org/notebooks/02_using_basemaps
- https://leafmap.org/notebooks/26_kepler_gl
- https://leafmap.org/notebooks/65_sagemaker
- https://leafmap.org/notebooks/26_kepler_gl
- https://leafmap.org/notebooks/29_pydeck
- https://leafmap.org/notebooks/58_bokeh
