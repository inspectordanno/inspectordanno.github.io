---
layout:      project
title:       A Visual Insight into American Craft Beers
date:        24 Aug 2018
screenshot:
  src:       /img/beer/beer_1920.png
  srcset:
    1920w:   /img/beer/beer_1920.png
    960w:    /img/beer/beer_960.png
    480w:    /img/beer/beer_480.png
caption:     American craft beers and breweries, organized by state.
description: American craft beers and breweries, organized by state.
links:
  - title:   View Project
    url:     ../../project_code/craft_beer_viz/dist/index.html
  - title:   Github
    url:     https://github.com/inspectordanno/craft_beer_viz
featured:    true
---
>For best experience, please view on desktop.

This is the project I'm most proud of. It is a classic data visualization “dashboard”. Sometimes I cringe when I hear that word, but it's definitely the best way to describe this work. The user selects a parameter and then all the modules update based on the input. 

In this example, the parameter selected is a state. When the user clicks on a state, the dataset (consisting of breweries and beers) is filtered down to the state level. The charts track two important summary statistics of beer: alcohol by volume and IBU. The higher a beer is in IBU, the more bitter.

After the user selects a state, they can select another or click the existing state to go back to the country-level.

## Beginning Stumbling Blocks

 Aft first, I wanted to implement a shopping cart experience where the user browses a selection of beers by type and then picks the ones they like. However, when I started making this project, I realized it was a lot more useful to summarize data from a top-down level. D3.js (the standard JS data viz library) is very good at making charts that can link to each other and animate data when a condition was met. As soon as I embarked on this path, I realized the power of D3.js (and gulp–dare I say raw JavaScript?) at manipulating data in the browser.

The other major roadblock in the beginning was that all the APIs for beer on the internet are not public. As a lone student, I couldn’t secure any API keys, so I had to rely on .csv files I found online. I think the quality of the data from a  API might be better than those of the .CSV I found, but it didn’t change my workflow much, since nearly all of my work in in front-end data manipulation and display.

## The Zoomable Map

I’m very proud I got the map to work. It uses a [complicated D3 zooming feature](https://bl.ocks.org/mbostock/9656675) that I really struggled with, but somehow got functional in the end. I also like that the map served as a handy controller to manipulate the rest of the data.

Each state is generated in SVG as a feature. When the user clicks on the feature, the map zooms in and passes filtered data to the charts.
