# hackathon2019


```python
import gmaps
import pandas as pd
gmaps.configure(api_key='AIzaSyB91zgXOWGWA4xM6oZ2FgiFvu9E_GuSiIk')
homeless_df = pd.read_csv("homeless.csv")
homeless_df = homeless_df[homeless_df['LATITUDE'].notnull()]
homeless_df = homeless_df[homeless_df['LONGITUDE'].notnull()]
homeless_df = homeless_df[['LATITUDE', 'LONGITUDE']]
homeless_layer = gmaps.symbol_layer(
    homeless_df, fill_color='rgba(3, 156, 39,0.1)',
    stroke_color='rgba(0,102,102,1)', scale =2
)

healthFacilities_df = pd.read_csv("healthFacilities.csv")
healthFacilities_df = healthFacilities_df[healthFacilities_df['latitude'].notnull()]
healthFacilities_df = healthFacilities_df[healthFacilities_df['longitude'].notnull()]
healthFacilities_df = healthFacilities_df[['latitude', 'longitude']]
healthFacilities_layer = gmaps.symbol_layer(
    healthFacilities_df, fill_color='rgba(0, 102, 102,0.1)',
    stroke_color='rgba(139, 0, 139,1)', scale =2
)

fig = gmaps.figure()
fig.add_layer(homeless_layer)
fig.add_layer(healthFacilities_layer)
fig
```


    Figure(layout=FigureLayout(height='420px'))

