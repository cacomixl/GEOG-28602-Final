# GEOG-28602-Final
Work for my final project in GIS III: A Basemap for Asian America

## Goals
Broadly, I want to use Mapbox to create a map that portrays and grounds Asian-Americans. I want to use this map as a way of discovering elements of Asian-American cultures that I'd never been exposed to before. I intend for this to be an empowering project for myself, and perhaps other Asian-Americans, in terms of being visible in the cartographic tradition. Initially, I'd looked into creatinga complex web of Asian cultural stories and sites, but I've found that Mapbox (at least Mapbox Studio) is fairly limited in the number and type of data visualizations you can put in. It is good, however, at handling large quantities of data and making them look pretty, both of which feed in well to the idea of making a dot map of Asian-Americans in the US. After doing all of the heavy data wrangling, I hope to make it all look good, and represent 

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
I referenced Jia Zhang's work at the Center for Spatial Research in making an Asian-American basemap (visible at https://medium.com/uncharted-singles/asian-american-dot-density-map-84271a4e68cd), but diverged from her methods in generating random dots for the basemap. For the random dot generation, I relied upon various online tutorials, the most prominent being that of Cornell GIS (at https://www.youtube.com/watch?v=TOY_7xKtTcU).

I was not able to upload some of the files to the repo, as they were too big (even when zipped), but you can access the randomly placed dots used to make the Mapbox map (_All Asian Dots_), the tract-level shapefile of the entire US containing population counts for each Asian subgroup (_Full Asian Tracts_), and a QGIS file putting them together at the following Google Drive link: https://drive.google.com/drive/folders/1KMuf1umuicS5Gp1eg3B0XmReND1fsdE-?usp=sharing

Another limitation of Mapbox was that I could only display seven groupings and colors of dots at a time. I'm not sure why they had this limit, but I did the best with what I had, grouping Asian-American communities (East Asian, Southeast Asian, South Asian) with similar languages and nearby homelands together, in addition to listing the four most common Asian-American ancestries (Chinese, Indian, Filipino, Vietnamese) as standalone groups. I then tried to give nearby natiolies similar colors, yet ones that would pop next to each other. Since I was using a dark basemap, I figured cyan, magenta, and yellow would be the most visible, so I assigned them to the three largest groups. Then, I issued slightly more subdued, yet still fully visible, colors to the rest of the divisions. After much trial and error with color, size, and opacity, I think I found a good balance.

## Results
The basemap can be viewed at https://api.mapbox.com/styles/v1/cacomixl/cl3w7e9qc00fb15l7geekmeke.html?title=view&access_token=pk.eyJ1IjoiY2Fjb21peGwiLCJhIjoiY2wyb2MydDhqMDRlZDNjbTh5bGJkNjZuYyJ9.Bb_yFaNZPLr63sO7AL_clQ&zoomwheel=true&fresh=true#5.71/33.124/-100.561/0/1




## Discussion
One pattern that I noticed while looking at the map as a whole was that Asian-Americans were often clustered quite heavily around cities. However, I wasn't sure whether that was just because Americans in general tend to be clustered in cities, or Asian-Americans were particuraly prevalent in them. As it turns out, Asian-Americans are indeed more concentrated in cities than American as a whole. Whereas Asian-Americans only make up 5.6% of the US population, they make up 9.7% of the population in counties labeled as "Large Central Metro". That percentage drops precipitously in less urban areas, with Asian-Americans comprising 2.2% of the population in "Small Metro" areas, 1.3% in "Micropolitan" areas, and only 0.6% in "Non-Core" areas.

![Asian Percents by Urban Code](https://user-images.githubusercontent.com/104388190/171604802-0c5d8163-d1ae-4694-916b-f1e437f59126.jpg)

This spatial distribution led me to wonder how urban/rural distribution varied by Asian ethnic group. After lots of typing in R, I got the table below. It revealed noticeable differences between Asian ethnic groups. Taiwanese-Americans were the most urban, with 51.5% living in "Large Central Metro" counties, closely followed by Chinese-Americans and Vietnamese-Americans. On the other end of the spectrum, Bhutanese, Hmong, and Laotian Americans all had "Large Central Metro" residence rates south of 30%, and higher residence in "Medium Metro" areas. There were also significant (>5% of national ethnic population) numbers of Burmese, Laotian, and Thai-Americans in rural "Non-Core" areas. Full data can be found below.

[cty_ethn_agg2.csv](https://github.com/cacomixl/GEOG-28602-Final/files/8822762/cty_ethn_agg2.csv)

One thing I struggled with was that, whatever I did, dots for certain ethnic groups tended to get placed on top of other dots, creating an illusion (when viewed from far enough away) that those groups have larger, denser populations than they do. I heard that tippecanoe for Mapbox might be a solution for this, but I was struggling to even get tippecanoe on my laptop at all, so I decided to simply deal with the fact of the uneven distribution. In this future I would like to find a solution to this, but in the meantime I still think it looks pretty and tells a story!


## Conclusion
