# Webscraping for Industry Cluster Analysis

Scraping data from US Bureau of Labor Statistics using beautiful soup and selenium modules

## Project Description:

The data task requires creation of industry cluster bubble charts, which are a common economic development research technique used to identify industries in which a region has a comparative advantage. This study analyzes twenty industry clusters at Ohio State along with Adams County in two ways: using location quotients (identify strengths and weaknesses in the region’s economy) and using shift-share analysis (identify the impact of region-specific factors on regional economic growth). An industry cluster bubble chart needs to be prepared for the State of Ohio, and then a separate chart for Adams County, Ohio.

## Data

The data for preparing cluster chart was obtained from Quarterly Census of Employment and Wages- Bureau of Labor Statistics. The data used for analysis consisted of annual average of employment, wage and location quotient column for private sector industry clusters. The industry clusters were based on the North American Industry Classification System (NAICS) codes. For the analysis, 20 industry clusters (NAICS sectors) were used for Ohio and US, whereas only 15 industry clusters were used for Adams county. The data for Adams country excluded rows with suppressed employment and wages, therefore only 15 clusters were used for analysis. Two years of data: 2015 and 2018 was used for the industry cluster analysis.

The data on the website was scraped using python, looping over the relevant pages of US, Ohio and Adams county to get private industry cluster data (employement information) from 2015 and 2018. The required information from the page was inspected using developer options in the browser. Beautiful soup is a great package while scraping data from static html page. But for dyanmaic pages, where there is delay to load data on the webpage, "selenium" triggers chroimum driver and then the data extraction takes place.

QCEW Data Views. Bls.gov. https://data.bls.gov/cew/apps/data_views/data_views.htm#tab=Tables. Published 2018. Accessed May 6, 2020.

## Dataset preparation for industry cluster analysis

The data was handled using excel. The scraped data were clean enough. Excel was used to calculate required values for Location Quotient (LQ), % change in LQ from 2015 -2018 and % change in employment from 2015-2018. Also, other numerical values were calculated using the formula below:

Location Quotient = [Eri/Er] / [Eni/En]

i.e. proportion of employment of industry cluster for region divided by nation

where,

- Eri = Employment of Industry Cluster i in Region
- Er = Employment of Region
- Eni = Employment of industry cluster in Nation
- En = Employment of Nation

Along with LQ, other values were also calculated other variables for share-shift analysis for Ohio State.

- National Share = % change in En \_ Eri (year 2015)
- Industry Cluster Share = (%change in Eni - %change in En) \_ Eri (2015-initial year)
- Regional Share = Actual change in Eri - [NS+IS]

After creating required variables, data was imported in python and after performing some basic data processing, an interactive industry cluster bubble chart was prepared using "plotly".

## Getting started

- Use webscraping.ipynb file to scrape data from the website.
- Inspect cleaned_data.xlsx file for the calculations.
- Use cleaned_for_cluster.xlsx file to create industry cluster bubble charts.
