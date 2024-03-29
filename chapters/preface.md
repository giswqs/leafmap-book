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

# Preface

## Introduction

This book is a comprehensive guide that empowers readers with the knowledge and skills to effectively visualize and analyze geospatial data using the leafmap Python package. Geospatial data plays a crucial role in various fields, making this book an invaluable resource for professionals, researchers, and enthusiasts who want to harness the full potential of geospatial data visualization and analysis.

With practical examples, step-by-step instructions, and insightful explanations, this book serves as an indispensable companion for unlocking the power of geospatial data. Readers will learn how to create visually stunning geospatial visualizations that captivate audiences and convey complex information with clarity. They will also gain proficiency in advanced analysis techniques, enabling them to extract meaningful insights from geospatial data.

One of the highlights of this book is the exploration of interactive web applications using leafmap. Readers will discover how to develop and deploy engaging web apps that allow users to interact with geospatial visualizations, thereby sharing their insights with a wider audience.

By the end of this book, readers will have the skills and confidence to tackle real-world geospatial challenges. They will be equipped with the tools to navigate the intricacies of acquiring, manipulating, and analyzing geospatial data, enabling them to make informed decisions and drive innovation in their respective fields.

## Who this book is for

Whether you're a seasoned data scientist looking to extend your skills into the geospatial domain, or a geographer eager to harness the power of modern data science, this book is suitable for you. This book is also suitable for anyone who would like to learn how to use Python to analyze and visualize geospatial data interactively in a Jupyter environment. It is particularly suited for novice users with limited programming skills. Advanced programmers can also find leafmap a useful tool for analyzing geospatial data and building interactive web apps.

## What this book covers

This book covers a comprehensive range of topics related to geospatial data visualization and analysis using the Leafmap Python package.

**Chapter 1** _Getting Started with Leafmap_: This chapter introduces the leafmap Python package and provides instructions on how to install it. Readers will learn about the key features of leafmap and how to create interactive maps using different plotting backends.

**Chapter 2** _Basic Map Visualization_: In this chapter, readers will be introduced to the fundamentals of map visualization. They will learn how to visualize vector and raster data interactively within a Jupyter environment. Additionally, the chapter covers the addition of widgets to maps, such as legends, colorbars, and labels.

**Chapter 3** _Getting Geospatial Data_: This chapter focuses on the process of acquiring geospatial data from various sources. Readers will explore different data sources, including cloud-computing platforms like Microsoft Planetary Computer and Amazon Web Services. They will learn how to obtain and integrate geospatial data into their analysis workflows.

**Chapter 4** _Working with Geospatial Data_: In this chapter, readers will learn how to manipulate geospatial data effectively. The topics covered include clipping, merging, and raster data manipulation techniques. Additionally, readers will discover how to create choropleth maps and heat maps to enhance their geospatial visualizations.

**Chapter 5** _Time Series Visualization_: This chapter is dedicated to visualizing time series data. Readers will gain insights into techniques for visualizing and analyzing time-dependent data. They will learn how to create engaging timelapse animations using both vector and raster data.

**Chapter 6** _Geospatial Data Analysis_: In this chapter, readers will explore advanced geospatial data analysis techniques. The chapter covers hydrological analysis, LiDAR data analysis, and zonal statistics. Readers will learn how to leverage whitebox and leafmap to perform these analyses effectively.

**Chapter 7** _Deep Learning Applications_: This chapter provides an introduction to deep learning applications in the geospatial domain. Readers will learn how to perform interactive image segmentation using leafmap and segment-geospatial. They will gain insights into the application of deep learning techniques for geospatial data analysis.

**Chapter 8** _Building Interactive Web Apps_: This chapter focuses on the development of interactive web apps using leafmap. Readers will learn how to build interactive web applications and deploy them to the cloud for public access. The chapter covers the necessary tools and techniques for creating compelling web-based geospatial applications.

## To get the most out of this book

This book assumes that you have some basic knowledge of Python. This means that you should be comfortable with the basic Python syntax, including variables, lists, dictionaries, loops, and functions. If you are familiar with creating lists and defining variables, and have worked with for loops before, you have sufficient Python knowledge to get started.

To get the most out of this book, it is highly recommended that you type the code yourself in a Jupyter environment, such as Jupyter notebook, JupyterLab, or Google Colab. This will aid your understanding of the code and the material in the book.

## Download Jupyter notebook examples

The Jupyter notebook examples for this book can be downloaded from the book’s GitHub repository at <https://github.com/giswqs/leafmap-book>. If there are any updates to the code, they will be made available in this repository.

## Conventions used

There are a number of text conventions used throughout this book.

`Code in text`: Indicates code words in text, folder names, filenames, file extensions, pathnames, URLs, etc. Here is an example: Set `API_KEY` as a system environment variable.

Python code blocks are set as follows:

```{code-cell}
import leafmap
# Create an interactive map
m = leafmap.Map(center=[40, -100], zoom=4)
m
```

**Bold**: Indicates a new term, an important word, or words that you see onscreen. For instance, words in menus or dialog boxes appear in bold. Here is an example: Click on **Advanced settings** to set `API_KEY` as an environment variable.

## Get in touch

We welcome feedback from our readers.

**Questions:** If you have any questions about the materials covered in the book, go to the book repository [discussion board](https://bit.ly/leafbook-qa) to ask questions and share ideas.

**Errata:** Although we have made every effort to ensure the accuracy of the book content, errors may occur. If you find any mistakes in the book, please report them to us. Please go to the book repository and [submit an issue](https://bit.ly/leafbook-issues).

## Acknowledgments

I would like to express my sincere gratitude to the individuals and organizations who have contributed to the creation of this book. In particular, I am indebted to my manager, Wenming Ye, at Amazon, where I served as a Visiting Academic. Their unwavering support and the environment they provided have been instrumental in shaping this work.

I would also like to extend my appreciation to the reviewers who dedicated their time and expertise to provide valuable feedback on this book. Your insights and suggestions have not only improved the quality of my work but have also made it more accessible to readers. Your contributions are deeply appreciated. A special thank you goes to Khalil Misbah for designing the [leafmap logo](https://github.com/opengeos/leafmap/tree/master/docs/assets).

Furthermore, I want to acknowledge the efforts of my editor and publishing team. Their dedication and hard work have been crucial in bringing this book to fruition. Their support and guidance throughout the process have been invaluable, and I am grateful for their expertise and commitment.

Lastly, I would like to express my heartfelt thanks to my family and friends. Your unwavering support and encouragement have been a constant source of strength throughout this endeavor. Your love and belief in me have kept me motivated during the challenging times, and I am forever grateful for your presence in my life.

To all those who have played a role, big or small, in the development of this book, I extend my deepest appreciation. Your contributions have made a significant impact, and I am honored to have had the opportunity to collaborate with such remarkable individuals.

Thank you.
