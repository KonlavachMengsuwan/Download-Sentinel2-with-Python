# Download-Setinel2-with-Python

## 1. Install sentinelsat package
```
conda install python=3 sentinelsat
```

## 2. Load library
```
from sentinelsat.sentinel import SentinelAPI, read_geojson, geojson_to_wkt
from datetime import date
```

## 3. Register and Login to Corpernicus Open Access Hub
```
https://scihub.copernicus.eu/dhus/#/home
```

## 4. Connect to API
```
api = SentinelAPI('user', 'password', 'https://scihub.copernicus.eu/dhus')
```

## 5. Create Footprint from GeoJSON Polygon
```
footprint = geojson_to_wkt(read_geojson('./map_aoi.geojson'))
```

## 6. Select Date, Platform, Cloudcover
```
products = api.query(footprint,date = ('20180101', '20190826'),
platformname = 'Sentinel-2',cloudcoverpercentage=(0, 30))
```

## 7. Convert geoJSON to Pandas DataFrame
```
products_df = api.to_dataframe(products)
```

## 8. Check geometry of products
```
api.to_geojson(products)
```

## 9. Download single scene by known product id
```
api.download(<product_id>)
```

## 10. Unzip
```

```

## 11. Plot with gdal or rasterio
```
with rio.open(‘sentinel2B_june2019.tif’) as src :
 fig, ax = plt.subplots()
 rio.plot.show(src, ax=ax, title=’Stack Bands’)
```



