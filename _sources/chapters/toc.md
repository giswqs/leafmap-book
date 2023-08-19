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

# Table of Contents

- [Chapter 1: Getting Started with Leafmap](https://book.leafmap.org/chapters/1_get_started.html)
- [Chapter 2: Basic Map Visualization](https://book.leafmap.org/chapters/2_data_viz.html)
- [Chapter 3: Getting Geospatial Data](https://book.leafmap.org/chapters/3_get_data.html)
- [Chapter 4: Working with Geospatial Data](https://book.leafmap.org/chapters/4_work_with_data.html)
- [Chapter 5: Time Series Visualization](https://book.leafmap.org/chapters/5_time_series.html)
- [Chapter 6: Geospatial Data Analysis](https://book.leafmap.org/chapters/6_data_analysis.html)
- [Chapter 7: Deep Learning Applications](https://book.leafmap.org/chapters/7_deep_learning.html)
- [Chapter 8: Building Interactive Web Apps](https://book.leafmap.org/chapters/8_web_apps.html)

<!-- Title: Exploring Geospatial Data Visualization with Leafmap: A Comprehensive Guide

Alternative title: Exploring Geospatial Data Visualization with Leafmap: A Hands-On Approach

Introduction:

The importance of geospatial data visualization in various fields.
The role of Python in geospatial data analysis and visualization.
Introduction to the Leafmap Python package as a powerful tool for interactive geospatial data visualization.

Chapter 1: Getting Started with Leafmap

What is Leafmap: Overview and features.
Installing Leafmap and its dependencies.
Setting up your development environment.
Quickstart example: Creating a simple interactive map.

Introduction
Installation
Colab, AWS, and Planetary Computer
Plotting backends
Using basemaps

https://leafmap.org/notebooks/01_leafmap_intro
https://leafmap.org/notebooks/02_using_basemaps
https://leafmap.org/notebooks/26_kepler_gl
https://leafmap.org/notebooks/65_sagemaker
https://leafmap.org/notebooks/26_kepler_gl
https://leafmap.org/notebooks/29_pydeck
https://leafmap.org/notebooks/58_bokeh


Chapter 2: Basic Map Visualization

Understanding the map widget and its components.
Adding base maps and adjusting map styles.
Placing markers, popups, and labels on the map.
Layer controls and layer management.+

https://leafmap.org/notebooks/27_basemap_gallery
https://leafmap.org/notebooks/03_cog_stac
https://leafmap.org/notebooks/05_load_raster
https://leafmap.org/notebooks/10_add_vector
https://leafmap.org/notebooks/06_legend
https://leafmap.org/notebooks/07_colorbar
https://leafmap.org/notebooks/11_linked_maps
https://leafmap.org/notebooks/12_split_map
https://leafmap.org/notebooks/23_colormaps
https://leafmap.org/notebooks/36_add_labels
https://leafmap.org/notebooks/59_create_legend
https://leafmap.org/notebooks/19_map_to_html



Chapter 3: Getting Geospatial Data

https://leafmap.org/notebooks/15_openstreetmap
https://leafmap.org/notebooks/17_vector_tile_layer
https://leafmap.org/notebooks/18_point_layer
https://leafmap.org/notebooks/30_census_data
https://leafmap.org/notebooks/31_search_basemaps
https://leafmap.org/notebooks/37_planetary_computer
https://leafmap.org/notebooks/42_create_cog
https://leafmap.org/notebooks/45_create_vector
https://leafmap.org/notebooks/46_edit_vector
https://leafmap.org/notebooks/47_numpy_to_cog
https://leafmap.org/notebooks/56_download_ned
https://leafmap.org/notebooks/57_national_map
https://leafmap.org/notebooks/64_stac_search
https://leafmap.org/notebooks/68_openaerialmap
https://leafmap.org/notebooks/69_turkey_earthquake
https://leafmap.org/notebooks/71_aws_s3
https://leafmap.org/notebooks/73_custom_stac
https://leafmap.org/notebooks/74_tms_to_geotiff
https://leafmap.org/notebooks/78_read_raster

Chapter 4: Working with Geospatial Data

Loading and displaying different geospatial data formats (shapefiles, GeoJSON, raster data, etc.).
Styling vector and raster data layers.
Applying symbology, color maps, and transparency.
Handling projections and coordinate systems.


https://leafmap.org/notebooks/09_csv_to_points
https://leafmap.org/notebooks/13_geopandas/
https://leafmap.org/notebooks/14_postgis
https://leafmap.org/notebooks/32_local_tile
https://leafmap.org/notebooks/34_add_points_from_xy
https://leafmap.org/notebooks/39_inspector_tool
https://leafmap.org/notebooks/41_raster_gui
https://leafmap.org/notebooks/43_search_control
https://leafmap.org/notebooks/49_split_control
https://leafmap.org/notebooks/50_marker_cluster
https://leafmap.org/notebooks/53_choropleth
https://leafmap.org/notebooks/24_heatmap
https://leafmap.org/notebooks/54_plot_raster
https://leafmap.org/notebooks/76_image_comparison
https://leafmap.org/notebooks/33_image_overlay
https://leafmap.org/notebooks/60_add_widget


Chapter 5: Time Series Visualization

Visualizing temporal geospatial data.
Creating time-based animations and sliders.
Handling time series data for effective storytelling.

https://leafmap.org/notebooks/20_planet_imagery
https://leafmap.org/notebooks/21_ts_inspector/
https://leafmap.org/notebooks/22_time_slider
https://leafmap.org/notebooks/20_planet_imagery
https://leafmap.org/notebooks/61_vector_to_gif
https://leafmap.org/notebooks/72_timelapse



Chapter 6: Geoprocessing and Analysis

Introduction to geoprocessing functions within Leafmap.
Performing spatial queries and selections.
Buffering, intersecting, and overlaying spatial datasets.
Calculating spatial statistics and attributes.

https://leafmap.org/notebooks/08_whitebox
https://leafmap.org/notebooks/48_lidar
https://leafmap.org/notebooks/55_lidar

https://leafmap.org/notebooks/63_arcgis
https://leafmap.org/notebooks/70_zonal_stats
https://leafmap.org/notebooks/77_split_raster

Chapter 7: Deep Learning with Leafmap

https://leafmap.org/notebooks/75_segment_anything



Chapter 8: Web Mapping Applications

Building web mapping applications using Leafmap.
Integrating Leafmap with other web frameworks (Flask, Django, etc.).
Deploying interactive maps online.



Chapter 9: Customization and Advanced Techniques

Customizing map elements using HTML and CSS.
Incorporating external libraries for advanced data visualization.
Creating custom legends, tooltips, and map interactions.

Chapter 10: Case Studies

Real-world examples showcasing the diverse applications of Leafmap.
Environmental monitoring, urban planning, agriculture, and more.
Step-by-step walkthroughs of complex visualizations.

Chapter 12: Tips and Best Practices

Performance optimization for large datasets.
Writing clean and modular Leafmap code.
Ensuring responsive design for various devices.
Debugging common issues and errors.

Chapter 12: Future Developments and Community Contributions

Exploring the future roadmap of Leafmap.
Contributing to the Leafmap community.
Staying up-to-date with the latest enhancements.
Conclusion:

Recap of the key concepts covered in the book.
Encouragement for readers to continue exploring geospatial data visualization.
Final thoughts on the potential of Leafmap in advancing geospatial analysis.
Appendices:

Installation guide for required software and packages.
Additional resources for further learning and exploration.
Glossary of key terms and concepts. -->
