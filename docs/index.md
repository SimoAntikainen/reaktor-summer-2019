# Reaktor machine-learning preliminary assignment

Full repository with code available at: [https://github.com/SimoAntikainen/reaktor-summer-2019](https://github.com/SimoAntikainen/reaktor-summer-2019)


## Excersise 1

<div>
{% include_relative small-multiples-excersise1.html %}
</div>

Small multiples visualization should offer an easy way to compare the different gathered data types and work with small mobile device screens. 
Idea was to show the biggest factor in climate change against factors, which do not explain the long upward trend. Plotly interactive visualization library
was used as it makes building the plots fast in python and javascript. 

Data sources used allow their free use as long as they are properly referenced:

GISTEMP Team, 2019: GISS Surface Temperature Analysis (GISTEMP). NASA Goddard Institute for Space Studies. Dataset accessed 18 Feb 2019 at https://data.giss.nasa.gov/gistemp/.
Hansen, J., R. Ruedy, M. Sato, and K. Lo, 2010: Global surface temperature change, Rev. Geophys., 48, RG4004, doi:10.1029/2010RG000345.

Dr. Pieter Tans, NOAA/ESRL (www.esrl.noaa.gov/gmd/ccgg/trends/) and Dr. Ralph Keeling, Scripps Institution of Oceanography (scrippsco2.ucsd.edu/). Dataset accessed 18 Feb 2019

NOAA. Dataset accessed 18 Feb 2019 at https://origin.cpc.ncep.noaa.gov/products/analysis_monitoring/ensostuff/detrend.nino34.ascii.txt.

Sunspot data from the World Data Center SILSO, Royal Observatory of Belgium, Brussel. Dataset accessed 18 Feb 2019 at http://www.sidc.be/silso/datafiles#total. 

## Excersise 4

<div>
{% include_relative prediction-excersise4.html %}
</div>

For prediction an ARIMA time-series model was used as it is familiar with me through coursework. Pro's of this model are that it is easily explainable as the prediction depends only on the past values of temperature anomaly. The prediction itself is a straight line, because statistical testing did not indicate a seasonal component in the temperature anomaly. The model also takes a little time to fit and predict. 

Cons's of the model are related to the fact that it cannot take into account any exogenous data such as rising co2 concentration and solar activity. This is responsible for the low value of the prediction compared to other estimates. For this we could extend the model
from ARIMA to ARIMAX (X for exogenous variables such as CO2 concentration), but then we would have to also make predictions on these exogenous variables, which add a degree of uncertanty to the model I do not have the expertice to evaluate. 

I have an separate repository of these models with exogenous variables at [https://github.com/SimoAntikainen/sarimax-climate-change-forecast](https://github.com/SimoAntikainen/sarimax-climate-change-forecast). 

## Excersise 5

Simplest way to deliver the service would be to once a month
run a server-side python script with cron, Heroku scheduler etc, which scrapes new data from the sources and calculates new predictions based on this data. 

Then we could either update the Plotly.py visualization html files server side 
and serve them to the client, but this is not very economical because of the large file size of the created visualizations (around 2.8 mb). Therefore, a more economical option is to probably serve the data to the front-end via a REST-api (resource/temperature, resource/anomaly etc.) and use Plotly.js JavaScript library to build the charts client side. Translating these charts from Plotly.py to Plotly.js should not take a long time from experience and should offer greater flexibility in customizing the charts for mobile devices. 







