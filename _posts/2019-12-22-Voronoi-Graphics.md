---
layout: post
title: 'Voronoi Graphics: Drawing shapes across voronoi edges'
date: 2019-12-22 14:37:40
description: Generate 2d map terrain on voronoi diagrams
tags: gamedev maths
categories:
---
Today I generated and drew onto a voronoi diagram using the [Voronoi](https://github.com/mdally/Voronoi) (mdally/Voronoi) library.

## Generating the diagram

The first thing I'd have to do is generate a voronoi diagram, this can be done as follows.

### Generate random points

First up I just generate a set of random points across a set area, I generated 10,000 points across an area of 1280x720.

### Apply Fortunes algorithm using the voronoi library

Using the library's VoronoiDiagramGenerator, I can pass it the sites, and a box which will provide the edges of our diagram (again being 1280x720).

### Lloyds Relaxtion

We then use the library to apply Lloyds Relaxation to our voronoi, which simply runs fortunes algorithm across all the cell sites in the previous voronoi, this will generate a slightly more organized voronoi diagram.

## Generating Shapes

Next we can generate shapes across this diagram, this will be done by giving each cell a struct containing their altitude (more info to aid with world generation can be added later), if their altitude is 0 it's water otherwise it is land. We store this cell data in a map, using cells as the key to this map.

`std::map<Cell*, MapCell*> cellproperties;`

### Drawing the intersections between water and land

Finally, to find the edges to draw, we iterate through every edge in the diagram, if one of the cells on either the left or right isn't 0 and the other is 0 then we add the line to a sf::VertexArray that draws lines.

![Voronoi circle](https://imgur.com/2d38bab6-a253-436c-82b4-e49d3073195a)
