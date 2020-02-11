---
layout:      project
title:       Which College Graduates Make the Most?
date:        20 Nov 2019
screenshot:
  src:         /img/college/college.gif
  # srcset:
  #   1920w:   /img/media/media_1920.png
  #   960w:    /img/media/media_960.png
  #   480w:    /img/media/media_480.png
caption:     A WSJ project visualizing debt and income among U.S. universities.
description: A WSJ project visualizing debt and income among U.S. universities.
links:
  - title:   Launch Project
    url:     https://www.wsj.com/articles/which-college-graduates-make-the-most-11574267424
  # - title:   Github
  #   url:     https://github.com/inspectordanno/titanic_survival
featured:    true
---
>WSJ has a fairly strict paywall. If you can't see the project, contact me for a live demo!

This was my favorite project at the Wall Street Journal and also the most challenging. It is a scatterplot comparing income and debt for every university and college in the United States, by major.

The data was released by the Department of Education, and marked the first time that debt and income were released at the major level. The project took months of planning and execution. Constant design iteration yielded a simple data visualization, the time-tested scatteplot. There are also a few carefully placed annotations, radio buttons, and dropdown menus. There are thousands of school-major combinations that the user can pick, which made this project very customizable. It got millions of views and was a very shareable story that stressed reader participation. Fiddling is what interactive journalism should be, after all!

The data filtering is entirely powered by React and Redux, which made it easy to store the filtering options in a single source of truth. The scatterplot is also a React component, but required direct access to the DOM via ```d3.select()```. 

To achieve direct access to the DOM, I used a ```useEffect()``` hook, combined with a React ref. I learned this pattern from a very helpful [tutorial](https://medium.com/@jeffbutsch/using-d3-in-react-with-hooks-4a6c61f1d102) by Jeff Butsch.

~~~js

import React, { useRef, useEffect } from 'react';
import * as d3 from 'd3';

const Scatterplot = ({ filteredData }) => {

  const d3Container = useRef(null);

  useEffect(() => {
    //this is where the D3 DOM manipulation logic occurs

    if (filteredData && d3Container.current) {
       d3.select(d3Container.current)
        .append('g')
        .selectAll('.circle')
        .data(filteredData)
      
      //do more d3 stuff
    }
  }, [filteredData, d3Container.current]) //dependency array - block runs after any of these variables change;

  return (
    //d3 container
    <svg
      width="500"
      height="500"
      ref={d3Container}
    >
    </svg>
  );
};
~~~
