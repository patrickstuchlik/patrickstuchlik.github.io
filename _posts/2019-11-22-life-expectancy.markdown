---
layout: default
title: Life in St. Louis, MO
description: A machine learning investigation into life expectancy and features of the environment around us in my hometown
categories: machine learning
---

# Life Expectancy and the Built Environment in Saint Louis, Missouri

Below, you, a constitutuent or resident of the city of Saint Louis, Missouri, will find a tool under development to measure the relationship between public health and the built environment. What is the [built environment](https://en.wikipedia.org/wiki/Built_environment)? The "built environment" a catch-all term for features of your local area, built by humans, for the purposes of work, life, or play. Classic definitions include public parks and public transit, but researchers now include many more quantifiable features, including bicycling, healthy food access, and even mental health. For this tool, I have gathered data on at least seven aspects of the built environment.

It is intuitive and uncontroversial that built environment features have an effect on public health. Proximity to a public park encourages more walking, and more cardiorespiratory fitness is better for public health. This is a burgeoning area of study in public health research, with rigorous tools for quantifying the built environment still being vetted, but scholars have already [noted](https://www.ncbi.nlm.nih.gov/pubmed/27755063) effects in public health. The future is certain: more effects, and more specific effects, will be determined in this relationship.

What does that matter to you, a resident of St. Louis, though? First of all, most of these features of the built environment are built and maintained using your public dollars. You deserve the opportunity to see the impact of your (and all of our) spending. Secondly, and more importantly I would argue, we need to shine a light on [disparities](https://www.healthypeople.gov/2020/about/foundation-health-measures/Disparities) in public health, note if there's a relationship with disparities in public investment, and strive to spend the public health dollars of a government "for the people, by the people" on improving the public health of all its constituents.

Specifically, we are measuring the association of the features of the built environment with public health in St. Louis, MO. Public health is life expectancy, in years, measured by the NCHS's USALEEP project for each census tract (see below for links to data). Census tracts are a small geographic unit determined by the [census bureau](https://www2.census.gov/geo/pdfs/reference/GARM/Ch10GARM.pdf); consider that the city of St. Louis, with 300,000+ residents, has 106 census tracts. The built environment is measured through a combination of public or community gardens (both conventional community gardens as well as the city's Milkweed for Monarchs program), public transit (as measured by number of light rail stations in each census tract), length of bike lanes and area of public parks in a census tract, and a scaled score from the EPA measuring "walkability." I have also included a proxy measure of socioeconomic status (SES) because it plays such a large role in this association: percent of the adult population in each census tract without health insurance.

I began by reading in my collected data. 
*   **'GEOID'** : the 11-digit FIPS code for each census tract
*   **'land_perc'** : the percent of each census tract that GIS calculated to be land (i.e. not water)
*   **'food1'** : a USDA calculated percentage of the total census tract with [low access to healthy food](https://www.ers.usda.gov/data-products/food-access-research-atlas/documentation/) within 1 mile
* **'food2'** : similarly, the percentage of the low-income population in the census tract with low access to healthy food within 1 mile
* **'life'** : [life expectancy](https://www.cdc.gov/nchs/nvss/usaleep/usaleep.html), in years, at birth for the census tract
* **'mw'** : number of [milkweed gardens](https://www.stlouis-mo.gov/monarchs/) in each census tract, planted to encourage the monarch butterfly population
* **'cg'** : number of [community gardens](http://www.gatewaygreening.org/resources/map-of-gardens/) in each census tract
* **'metrolink'** : number of [Metrolink](https://www.metrostlouis.org/developer-resources/) (light rail) stations in each census tract
* **'tract_area'** : area (units unclear due to GIS projection issues) of each census tract
* **'bike_len'** : total length of [bike lanes](https://www.stlouis-mo.gov/government/departments/street/streets-sidewalks-traffic/bicycling/bike-routes-and-maps.cfm) for each census tract
* **'bike_cnt'**: total segments of bike lanes for each census tract
* **'park1'** : total area of [parks](https://www.stlouis-mo.gov/data/parks.cfm) in each census tract (for similar reasons, units unclear)
* **'park1ratio'** : ratio of park1 / tract_area => the ratio of a census tract that is public parks
* **'park2' , 'park2ratio'** : a different (and inferior) polygon intersection tool was used in GIS to compute these park areas, in the same schema as park1 and park1ratio
* **'walk'** : National Walkability Index from the [EPA](https://www.epa.gov/smartgrowth/smart-location-mapping#walkability) Note that these scores are provided for census block groups, so these have been averaged over tracts here
* **'unins'**: percentage of the adult non-institutionalized population without health insurance in each census tract, from [Census American FactFinder](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml)

Next I present an initial histogram of life expectancy in St. Louis. ![Hist](/assets/capstone/histogram1.png)

