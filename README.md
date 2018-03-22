# spatial_mapping
Simple ways to create spatial plots in python

## Exploring the gmplot package
Using publically available data from data.gov to create spatial heatmaps

```python
gmap = gmplot.GoogleMapPlotter.from_geocode("Minneapolis",12)
gmap.heatmap(df['geometry.y'], df['geometry.x'])
gmap.draw("./Output/snow_plow_2017.html")
```

![Minneapolis Snow Plow 2017 data](https://github.com/shubhstiws/spatial_mapping/blob/master/Minneapolis_Snow_plow_2017.PNG)
