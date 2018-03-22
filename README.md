# spatial_mapping
Simple ways to create spatial plots in python

## Exploring the gmplot package
Using publically available data from data.gov to create spatial heatmaps

### Getting data from data.gov

```python
import json
url = 'https://services.arcgis.com/afSMGVsC7QlRK1kZ/arcgis/rest/services/Snow_Emergency_Jane_Tows_2017/\
FeatureServer/0/query?where=1%3D1&outFields=*&outSR=4326&f=json'
with urllib.request.urlopen(url) as url:
    s = url.read()

df = pd.io.json.json_normalize(json.loads(s)['features'])
```
### Generate plot from a pandas dataframe with latitudes and longitudes

```python
gmap = gmplot.GoogleMapPlotter.from_geocode("Minneapolis",12)
gmap.heatmap(df['geometry.y'], df['geometry.x'])
gmap.draw("./Output/snow_plow_2017.html")
```
### Minneapolis Snow Plow 2017 heatmap
![Minneapolis Snow Plow 2017 data](https://github.com/shubhstiws/spatial_mapping/blob/master/Minneapolis_Snow_plow_2017.PNG)

### Using offline csv file
```python
import pandas as pd
df = pd.read_csv('./Data/Public_311_2017.csv')
```

### Minneapolis 311 calls 2017 heatmap
![](https://github.com/shubhstiws/spatial_mapping/blob/master/Minneapolis_311_calls_2017.PNG)

### Next Steps

* [ ] Plot the chicago crime dataset for diferent years to observe change in crime in different years
* [ ] Animate the change in heatmaps using imageio
* [ ] Explore other packages
