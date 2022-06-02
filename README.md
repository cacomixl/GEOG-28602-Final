# GEOG-28602-Final
Work for my final project in GIS III: A Basemap for Asian America

## Goals


## Background
D’Ignazio and Klein’s Feminist Data Visualization paper provides a theoretical foundation for this research project. While Asian-Americans and women certainly face different issues, in society in general and in the field of data visualization, the ethos of critical cartography in viewing maps as “historically and culturally contingent documents” holds significance intersectionally (D’Ignazio 2). Maps (especially in America) have historically been created by and for a white audience, and this, consciously or unconsciously, affects the way in which maps are presented. This project aims to provide a preliminary investigation into what it looks like to intentionally portray an Asian-American perspective on the US, perhaps as a counter to the standardization of whiteness.

My intention in highlighting different Asian-American ethnic groups in this project is to counteract a common perception of Asian-American sameness: it is be wrong, and an erasure of cultural uniqueness, to claim a common experience among Asian-Americans, and the term itself is quite problematizable. That being said, there are some benefits to this grouping, mostly having to do with the external perception of Asian-Americans more generally. Those commonalities provide the basis for the overarching theme of the project.

In particular, I felt that a dot map would be fitting for a project such as this

## Data Sources
I used 5-year ACS average data from 2016-2020, acquired via the Census's Social Explorer page. In particular, I chose the “Asian Alone Or In Any Combination By Selected Groups” table, which had all of the data I needed. However, this was just a table, not spatial data, so I took the tract-level TIGER files for each state from the Census website. I also found urban/rural classifications for each US county from the CDC website. Lastly, I used the spData package to get a quick, well-organized shapefile of the entire US.

### Spatial Scale
I used tract-level data, as that is the smallest scale at which Asian-American ethnic data is available. Placing dots randomly within, say, a county, would not give specificity of the level of analysis where the reader could discern important spatial patterns. However, such a large volume of data can be overwhelming to someone wanting to perform analysis, so I used CDP-level searches to find leads toward interesting, story-worthy places. Moreover, urban/rural classification data seemed to only be available via the CDC on the county level, so I used that. I will discuss the limitations of this county-level data later.

### Temporal Scale
The census data comes from the 2016-2020 ACS 5-year estimate. I tried to get the most up-to-date data possible, and at first I tried to use 2020 census data, but it seems that ethnicity data for the 2020 census hasn't been published yet, so the ACS had to be sufficient. Regarding urban/rural classification, it seemed that the CDC had most recently published its classifications in 2013. However, I think this is okay, as the structure of a county uis nlikely to change that much in 10 years, especially in an era of relative stagnation in population, and 2013 data can be used to define the broadest of labels in 2022.

## Methods


## Results
The basemap can be viewed at https://api.mapbox.com/styles/v1/cacomixl/cl3w7e9qc00fb15l7geekmeke.html?title=view&access_token=pk.eyJ1IjoiY2Fjb21peGwiLCJhIjoiY2wyb2MydDhqMDRlZDNjbTh5bGJkNjZuYyJ9.Bb_yFaNZPLr63sO7AL_clQ&zoomwheel=true&fresh=true#5.71/33.124/-100.561/0/1


## Discussion
By and large, Asian-Americans live in urban areas

## Conclusion
