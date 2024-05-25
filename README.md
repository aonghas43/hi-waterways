# hi-waterways
Histon and Impington waterways

## Data sources


table:
|Data|Source|Copyright|Licence|other attribution|
|----|------|---------|-------|-----------------|
|1888-1913 OS 6-inch map|[National Library of Scotland(NLS)](https://maps.nls.uk/projects/api/#gb6inch)|[NLS non-commercial licence](https://maps.nls.uk/copyright.html#noncommercial)|[CC 4.0](https://creativecommons.org/licenses/by/4.0/)|OS County Series mapping at Six-Inch to the mile / 1:10,560 for the 2nd edition, dating between 1888-1913, 'Reproduced with the permission of the National Library of Scotland'|
|UK Ordnance Survey Open Rivers|[OS OpenRivers](https://osdatahub.os.uk/downloads/open/OpenRivers)|Ordnance Survey data © Crown copyright and database right 2023|[Open Government v3](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/), [OpenData licence](https://www.os.uk/opendata/licence)||
|UK Ordnance Survey Open vector map data(Surface Water Line, Surface Water Area)|[OS Open VectorMap](https://osdatahub.os.uk/downloads/open/VectorMapDistrict)|Ordnance Survey data © Crown copyright and database right 2023|[Open Government v3](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/), [OpenData licence](https://www.os.uk/opendata/licence)|
|Approximate track of Award drain 164 and 165|[Hihub 23rd March 2023](https://www.hihub.info/features/the-floodmobile-is-coming/)|[HiHub](https://www.hihub.info/policies/terms-of-website-use/)|||


```text
Our existing drainage

Our flood risks arise along the course of our two main surface water drains, and residents living in these areas are probably most at risk. These are known as:

Award Drain 164: This runs from south to north. It starts south of the A14, crosses NIAB land and enters the settlements at Villa Road. It goes past the old Infants School, under Station Road, past the north side of the war memorial and then goes in a culvert under the B1049, to The Brook.

Award Drain 165: This runs east to west and comes into the settlement between St Georges Way and Woodcock Close, then passes Merrington Place and Ambrose Way. It is then culverted under the B1049 south to The Brook. It exits between the old Institute/Korten building and Pages Close, runs behind the School Hill / Tesco site, under the St Andrews Centre and out along the north side of Park Lane.
```

## Data processing

### "Data of interest"

- The Public Drains, which make up "Award drain 164" and "Award drain 165"
- any named waterways down stream of these, as far as the River Great Ouse
- upstream sections of these named waterways back to source, as far as makes sense
- Public drain #13 (PD 13), which starts in H&I 
- Continuation of PD 13 to Milton coutry park and thence to the River Cam
- Portions of AD 165  in the VEctor Map data but not the Open Rivers data

### Noted inconsistencies in base data

The "Open Rivers data" is not 100% consistent with the "Vector Map" data.

- Not all portions of AD 165 and PD 13 are in the "Open Rivers data"
- The Ordnance Survey data is not 100% consistent with the 1888 6-inch map
    - track of Public drain up Water lane - 6-inch map shows it as being sometimes on LHS, sometimes RHS of road
	- missing sections of OS data vs 6-inch map, for track of Public Drain


### Process

All extracts are GeoJson : done by filtering the base data on name and/or map extent using QGIS

1. Set background to be the 1888 6-inch map
1. Extract sets of waterway_link to match extent of "Public Drain" marked on map
1. Extract other named watercourses which are of interest (downstream of the Public drain, or upstream parts of waterways which the drain feeds into)
   - Callow Brook
   - Beck Brook
   - Washpit Brook
   - New cut (at Cottenham)
   - Cottenham Lode
   - River Great Ouse
   - River Cam
1. Extract Surface water Areas of interest
   - matching AD 165
   - Public drain #13
1. Extract waterway_links of interest 
   - matching AD 165
   - Public drain #13
1. Group the named watercourses and also extract the hydro-nodes which mark junction points 


TODO

Merge data to simply record items as "feature" with either a link or area geometry and an optional name