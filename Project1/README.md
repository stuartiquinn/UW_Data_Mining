# 001 Capital Bike Share Project
May 5, 2016  

#Introduction / About the Data

The City of Seattle recently bought out the bike-share service Pronto, which was established in 2014. The membership of the program has continued to see declines over the previous two years, resulting in the $1.4M buy-out acquisition by the city. In order to identify areas to improve the program the city is hoping to determine factors that define a good station in other bike-share programs, specifically the Capital City Bikeshare in the DC, MD, VA area. The exercise will require defining and collecting attributes that drive or are indicative of high-usage as measured by number of rentals. 

<b><i> About the Data </b></i><br>
<ol>
<li> Source: Capital City Bikeshare</li>
<li> Time Period: Jan 1, 2015 - Dec 31, 2015 </li>
<li> Stations: 157</li>
<li> Zipcodes: 21 </li>
<li> Total Rentals: 2180215 </li>
<li> Variables: 83 </li>
</ol><br>

<b><i> Sources of Data </b></i>
The data comes from four separate sources: 
[Capital Bikeshare](https://www.capitalbikeshare.com/system-data),
[Open StreetMap](http://osmar.r-forge.r-project.org/),
[Google Maps API](https://developers.google.com/maps/documentation/geocoding/intro#Geocoding) and [NeighborhoodInfo](http://neighborhoodinfodc.org/index.html)<br>


From mapping the number of rentals we find that there is large distribution near the National Mall and reflecting pool, which also share proximity to a number of the national memorial monuments (Lincoln, Vietnam War, WWII and Korean War). Thus, it may be fairly likely that these sites contribute to our usage trends and deserve more exploration. 

Furthermore, we find in our table, that the majority of top rental stations occur in the warmer months, indicating weather influence on usage trends. In fact, on average, we find that there are more rentals in the warmer seasons across the entire data set. 

<!--html_preserve--><div id="htmlwidget-6963" style="width:100%;height:auto;" class="datatables"></div>
<script type="application/json" data-for="htmlwidget-6963">{"x":{"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25"],["Jefferson Dr &amp; 14th St SW","Columbus Circle / Union Station","Columbus Circle / Union Station","Jefferson Dr &amp; 14th St SW","Massachusetts Ave &amp; Dupont Circle NW","Columbus Circle / Union Station","Massachusetts Ave &amp; Dupont Circle NW","Massachusetts Ave &amp; Dupont Circle NW","15th &amp; P St NW","Thomas Circle","15th &amp; P St NW","Thomas Circle","New Hampshire Ave &amp; T St NW","14th &amp; V St NW","14th &amp; V St NW","New Hampshire Ave &amp; T St NW","Jefferson Dr &amp; 14th St SW","New York Ave &amp; 15th St NW","Eastern Market Metro / Pennsylvania Ave &amp; 7th St SE","Columbus Circle / Union Station","17th &amp; Corcoran St NW","8th &amp; H St NW","Eastern Market Metro / Pennsylvania Ave &amp; 7th St SE","15th &amp; P St NW","1st &amp; M St NE"],[38.78,13.67,13.8,37.66,18.07,12.19,18.95,15.6,12.61,16.31,13.45,16.52,10.88,12.8,13.09,11.05,36.82,31.19,13.83,11,12.25,19.41,15.23,11.71,15.72],["Summer","Summer","Spring","Spring","Summer","Autumn","Spring","Autumn","Summer","Summer","Spring","Spring","Summer","Summer","Spring","Spring","Autumn","Summer","Summer","Winter","Summer","Summer","Spring","Autumn","Summer"],[23601,22198,20765,20138,18598,17367,17167,13509,13333,12969,12373,12322,11296,11196,11039,10815,10499,10455,10309,10182,9965,9925,9636,9603,9556]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> </th>\n      <th>station</th>\n      <th>duration_mean</th>\n      <th>season</th>\n      <th>num_rentals</th>\n    </tr>\n  </thead>\n</table>","options":{"columnDefs":[{"className":"dt-right","targets":[2,4]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false},"callback":null,"filter":"none"},"evals":[]}</script><!--/html_preserve-->

<b><i> Figure 1: Get Geographic Distribution of Number of Rentals</b></i><br>

<!--html_preserve--><div id="htmlwidget-8814" style="width:864px;height:576px;" class="leaflet"></div>
<script type="application/json" data-for="htmlwidget-8814">{"x":{"fitBounds":[38.79163,-77.119766,38.995853,-76.909363],"calls":[{"method":"addTiles","args":["http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,"Default",{"minZoom":0,"maxZoom":18,"maxNativeZoom":null,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"continuousWorld":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap</a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA</a>"}]},{"method":"addWMSTiles","args":["http://maps2.dcgis.dc.gov/dcgis/services/DCGIS_DATA/Transportation_WebMercator/MapServer/WMSServer?request=GetCapabilities&service=WMS",null,"BikeTrails",{"styles":"","format":"image/png","transparent":false,"version":"1.1.1","crs":null,"attribution":"DCGIS/DOT","layers":""}]},{"method":"hideGroup","args":["BikeTrails"]},{"method":"addLayersControl","args":["Default","BikeTrails",{"collapsed":false,"autoZIndex":true,"position":"topright"}]},{"method":"addCircles","args":[[38.90572,38.9024,38.90572,38.895344,38.9172,38.912659,38.9155,38.895344,38.912719,38.897446,38.90093,38.912659,38.9126,38.915417,38.9126,38.895344,38.8997,38.915417,38.9172,38.915417,38.9126,38.895344,38.90304,38.912659,38.9155,38.8997,38.90304,38.899408,38.9126,38.90304,38.897446,38.912719,38.90572,38.928156,38.8997,38.8997,38.90093,38.917622,38.90572,38.897446,38.899408,38.928156,38.90093,38.90093,38.917622,38.912659,38.917622,38.928156,38.899408,38.90304,38.9172,38.9024,38.915417,38.9249,38.9155,38.917622,38.9024,38.899408,38.9249,38.928156,38.912719,38.9249,38.9155,38.9249,38.897446,38.9172,38.912719,38.899972,38.899983,38.899983,38.899983,38.903732,38.918155,38.910972,38.9057,38.900413,38.897274,38.918155,38.899972,38.90509,38.897195,38.903732,38.918155,38.894758,38.903732,38.910972,38.910972,38.899972,38.90509,38.897195,38.899972,38.918155,38.905707,38.899983,38.900412,38.897274,38.897195,38.9003,38.897195,38.903732,38.9057,38.894758,38.905707,38.919077,38.919077,38.89696,38.9057,38.90509,38.900413,38.89696,38.910972,38.894832,38.900412,38.894758,38.9003,38.89696,38.90509,38.900413,38.894832,38.89696,38.9003,38.905707,38.900413,38.919077,38.905707,38.919077,38.894832,38.897274,38.897274,38.900412,38.900412,38.894758,38.894832,38.9003,38.9057,38.889908,38.884,38.889988,38.887378,38.889908,38.889908,38.887378,38.8896,38.884,38.884,38.88732,38.889955,38.8803,38.8803,38.889908,38.887378,38.889988,38.8803,38.889955,38.87861,38.8743,38.8743,38.8743,38.8803,38.88732,38.889988,38.889955,38.8743,38.87861,38.884,38.886952,38.8896,38.886952,38.88732,38.886952,38.87861,38.8896,38.87861,38.88732,38.884,38.8896,38.889955,38.884,38.881185,38.881185,38.8851,38.8792,38.8763,38.887378,38.884,38.886952,38.8851,38.8792,38.881185,38.8763,38.8792,38.889988,38.8851,38.8763,38.8851,38.8763,38.884,38.8792,38.881185,38.894573,38.894514,38.897351,38.895914,38.894514,38.897351,38.897351,38.895914,38.894514,38.894851,38.894851,38.894851,38.895914,38.897857,38.897351,38.897222,38.895914,38.894851,38.897857,38.897857,38.894573,38.894573,38.894573,38.897222,38.897222,38.897222,38.897857,38.894514,38.903819,38.899632,38.899632,38.902,38.898069,38.898364,38.9059,38.903819,38.899632,38.9086,38.902,38.898069,38.902,38.898364,38.90985,38.898364,38.9059,38.9086,38.9059,38.905607,38.9059,38.898364,38.8991,38.9086,38.903819,38.902,38.898069,38.8991,38.899632,38.9086,38.903819,38.898069,38.905607,38.8991,38.90985,38.905607,38.8991,38.905607,38.90985,38.90985,38.902204,38.902204,38.902204,38.902061,38.902061,38.902204,38.902061,38.9003,38.902061,38.894722,38.9003,38.89968,38.89968,38.901539,38.9003,38.901539,38.9003,38.894722,38.894722,38.894722,38.901539,38.901539,38.89968,38.89968,38.9022212,38.90774,38.90774,38.916442,38.905126,38.9022212,38.9022212,38.90774,38.9022212,38.922649,38.916442,38.90849,38.90849,38.916442,38.916442,38.922649,38.922649,38.905126,38.90774,38.90375,38.922649,38.905126,38.905126,38.90375,38.90375,38.90849,38.90375,38.90849,38.955016,38.922581,38.922581,38.9066,38.934267,38.955016,38.922581,38.930282,38.9066,38.934267,38.9066,38.9066,38.930282,38.944551,38.944551,38.955016,38.922581,38.930282,38.930282,38.934267,38.955016,38.944551,38.944551,38.934267,38.912682,38.922925,38.91554,38.91554,38.917761,38.91554,38.9268,38.927872,38.920669,38.91554,38.917761,38.912682,38.916787,38.927872,38.922925,38.927872,38.926088,38.927872,38.920669,38.92333,38.912682,38.9268,38.922925,38.9176,38.9176,38.9268,38.920669,38.9268,38.926088,38.9176,38.92333,38.926088,38.920669,38.918809,38.916787,38.916787,38.912682,38.9121,38.918809,38.9154,38.9121,38.92333,38.9154,38.917761,38.923203,38.922925,38.918809,38.9154,38.916787,38.9154,38.9121,38.92333,38.923203,38.917761,38.923203,38.926088,38.918809,38.9121,38.9176,38.923203,38.928743,38.9308,38.929464,38.9308,38.9319,38.936043,38.9319,38.9319,38.9319,38.936043,38.929464,38.928743,38.9375,38.9375,38.928743,38.929464,38.9308,38.936043,38.936043,38.9308,38.929464,38.9375,38.928743,38.9375,38.942016,38.9418,38.9418,38.956432,38.942016,38.949662,38.956432,38.9418,38.9418,38.949662,38.947774,38.949662,38.942016,38.947774,38.956595,38.947774,38.949662,38.956595,38.956595,38.942016,38.947774,38.956432,38.956595,38.956432,38.943837,38.934881,38.934881,38.943837,38.954812,38.934881,38.934881,38.947607,38.947607,38.947607,38.943837,38.943837,38.954812,38.947607,38.954812,38.954812,38.938736,38.938736,38.938736,38.938736,38.932514,38.927497,38.9346,38.932514,38.9346,38.933668,38.927497,38.932514,38.932514,38.927497,38.9346,38.933668,38.9346,38.933668,38.933668,38.927497,38.927095,38.927095,38.927095,38.927095,38.889935,38.878,38.884085,38.897063,38.889935,38.897063,38.878,38.894,38.889935,38.878,38.897063,38.897063,38.894,38.894,38.901385,38.884085,38.889935,38.901385,38.901385,38.884085,38.901385,38.894,38.878,38.8692,38.8692,38.867373,38.862669,38.862669,38.8692,38.862669,38.866611,38.862669,38.867373,38.865784,38.863897,38.867373,38.865784,38.863897,38.865784,38.86559,38.86559,38.865784,38.86559,38.8692,38.863897,38.86559,38.8601,38.8601,38.8601,38.8601,38.866611,38.866611,38.866611,38.873057,38.873057,38.873057,38.873057,38.867373,38.863897,38.87675,38.88412,38.87675,38.87675,38.88412,38.87675,38.8767,38.8767,38.8767,38.88412,38.888553,38.88412,38.8767,38.888553,38.888553,38.888553,38.844711,38.844711,38.844711,38.844711,38.843222,38.843222,38.843222,38.843222,38.90276,38.906602,38.906602,38.908142,38.9101,38.903407,38.903407,38.908905,38.903584,38.90276,38.903407,38.904742,38.904742,38.903407,38.906602,38.908142,38.908142,38.908142,38.903584,38.903584,38.908905,38.908905,38.908905,38.9101,38.906602,38.90276,38.9101,38.904742,38.903584,38.90276,38.9101,38.904742,38.90534,38.903827,38.903827,38.90088,38.90088,38.90534,38.90088,38.903827,38.9008,38.90088,38.903827,38.9008,38.9008,38.9008,38.90534,38.90534,38.8963,38.8963,38.8963,38.8963],[-77.022264,-77.02622,-77.022264,-77.016106,-77.0259,-77.017669,-77.0222,-77.016106,-77.022155,-77.009888,-77.018677,-77.017669,-77.0135,-77.012289,-77.0135,-77.016106,-77.023086,-77.012289,-77.0259,-77.012289,-77.0135,-77.016106,-77.019027,-77.017669,-77.0222,-77.023086,-77.019027,-77.015289,-77.0135,-77.019027,-77.009888,-77.022155,-77.022264,-77.02344,-77.023086,-77.023086,-77.018677,-77.01597,-77.022264,-77.009888,-77.015289,-77.02344,-77.018677,-77.018677,-77.01597,-77.017669,-77.01597,-77.02344,-77.015289,-77.019027,-77.0259,-77.02622,-77.012289,-77.0222,-77.0222,-77.01597,-77.02622,-77.015289,-77.0222,-77.02344,-77.022155,-77.0222,-77.0222,-77.0222,-77.009888,-77.0259,-77.022155,-76.998347,-76.991383,-76.991383,-76.991383,-76.987211,-77.004746,-77.00495,-77.0056,-76.982872,-76.994749,-77.004746,-76.998347,-76.9941,-76.983575,-76.987211,-77.004746,-76.997114,-76.987211,-77.00495,-77.00495,-76.998347,-76.9941,-76.983575,-76.998347,-77.004746,-77.003041,-76.991383,-77.001949,-76.994749,-76.983575,-76.9882,-76.983575,-76.987211,-77.0056,-76.997114,-77.003041,-77.000648,-77.000648,-77.00493,-77.0056,-76.9941,-76.982872,-77.00493,-77.00495,-76.987633,-77.001949,-76.997114,-76.9882,-77.00493,-76.9941,-76.982872,-76.987633,-77.00493,-76.9882,-77.003041,-76.982872,-77.000648,-77.003041,-77.000648,-76.987633,-76.994749,-76.994749,-77.001949,-77.001949,-76.997114,-76.987633,-76.9882,-77.0056,-76.983326,-76.995397,-76.995193,-77.001955,-76.983326,-76.983326,-77.001955,-76.9769,-76.995397,-76.995397,-76.983569,-77.000349,-76.9862,-76.9862,-76.983326,-77.001955,-76.995193,-76.9862,-77.000349,-77.006004,-77.0057,-77.0057,-77.0057,-76.9862,-76.983569,-76.995193,-77.000349,-77.0057,-77.006004,-76.995397,-76.996806,-76.9769,-76.996806,-76.983569,-76.996806,-77.006004,-76.9769,-77.006004,-76.983569,-76.9861,-76.9769,-77.000349,-76.9861,-77.001828,-77.001828,-77.0023,-76.9953,-77.0037,-77.001955,-76.9861,-76.996806,-77.0023,-76.9953,-77.001828,-77.0037,-76.9953,-76.995193,-77.0023,-77.0037,-77.0023,-77.0037,-76.9861,-76.9953,-77.001828,-77.01994,-77.031617,-77.022465,-77.026064,-77.031617,-77.022465,-77.022465,-77.026064,-77.031617,-77.02324,-77.02324,-77.02324,-77.026064,-77.026975,-77.022465,-77.019347,-77.026064,-77.02324,-77.026975,-77.026975,-77.01994,-77.01994,-77.01994,-77.019347,-77.019347,-77.019347,-77.026975,-77.031617,-77.0284,-77.031686,-77.031686,-77.03353,-77.031823,-77.027869,-77.0325,-77.0284,-77.031686,-77.0323,-77.03353,-77.031823,-77.03353,-77.027869,-77.034438,-77.027869,-77.0325,-77.0323,-77.0325,-77.027137,-77.0325,-77.027869,-77.0337,-77.0323,-77.0284,-77.03353,-77.031823,-77.0337,-77.031686,-77.0323,-77.0284,-77.031823,-77.027137,-77.0337,-77.034438,-77.027137,-77.0337,-77.027137,-77.034438,-77.034438,-77.04337,-77.04337,-77.04337,-77.038322,-77.038322,-77.04337,-77.038322,-77.0429,-77.038322,-77.045128,-77.0429,-77.041539,-77.041539,-77.046564,-77.0429,-77.046564,-77.0429,-77.045128,-77.045128,-77.045128,-77.046564,-77.046564,-77.041539,-77.041539,-77.059219,-77.071652,-77.071652,-77.0682,-77.056887,-77.059219,-77.059219,-77.071652,-77.059219,-77.077271,-77.0682,-77.063586,-77.063586,-77.0682,-77.0682,-77.077271,-77.077271,-77.056887,-77.071652,-77.06269,-77.077271,-77.056887,-77.056887,-77.06269,-77.06269,-77.063586,-77.06269,-77.063586,-77.069956,-77.070334,-77.070334,-77.05152,-77.057979,-77.069956,-77.070334,-77.055599,-77.05152,-77.057979,-77.05152,-77.05152,-77.055599,-77.063896,-77.063896,-77.069956,-77.070334,-77.055599,-77.055599,-77.057979,-77.069956,-77.063896,-77.063896,-77.057979,-77.031681,-77.042581,-77.03818,-77.03818,-77.04062,-77.03818,-77.0322,-77.043358,-77.04368,-77.03818,-77.04062,-77.031681,-77.028139,-77.043358,-77.042581,-77.043358,-77.036536,-77.043358,-77.04368,-77.0352,-77.031681,-77.0322,-77.042581,-77.0321,-77.0321,-77.0322,-77.04368,-77.0322,-77.036536,-77.0321,-77.0352,-77.036536,-77.04368,-77.041571,-77.028139,-77.028139,-77.031681,-77.0387,-77.041571,-77.0446,-77.0387,-77.0352,-77.0446,-77.04062,-77.047637,-77.042581,-77.041571,-77.0446,-77.028139,-77.0446,-77.0387,-77.0352,-77.047637,-77.04062,-77.047637,-77.036536,-77.041571,-77.0387,-77.0321,-77.047637,-77.012457,-77.0315,-77.027822,-77.0315,-77.0388,-77.024649,-77.0388,-77.0388,-77.0388,-77.024649,-77.027822,-77.012457,-77.0328,-77.0328,-77.012457,-77.027822,-77.0315,-77.024649,-77.024649,-77.0315,-77.027822,-77.0328,-77.012457,-77.0328,-77.032652,-77.0251,-77.0251,-77.032947,-77.032652,-77.027333,-77.032947,-77.0251,-77.0251,-77.027333,-77.032818,-77.027333,-77.032652,-77.032818,-77.019815,-77.032818,-77.027333,-77.019815,-77.019815,-77.032652,-77.032818,-77.032947,-77.019815,-77.032947,-77.077078,-77.072755,-77.072755,-77.077078,-77.082426,-77.072755,-77.072755,-77.079382,-77.079382,-77.079382,-77.077078,-77.077078,-77.082426,-77.079382,-77.082426,-77.082426,-77.087171,-77.087171,-77.087171,-77.087171,-76.992889,-76.997194,-76.9955,-76.992889,-76.9955,-76.991016,-76.997194,-76.992889,-76.992889,-76.997194,-76.9955,-76.991016,-76.9955,-76.991016,-76.991016,-76.997194,-76.978924,-76.978924,-76.978924,-76.978924,-76.93723,-76.9607,-76.957461,-76.947446,-76.93723,-76.947446,-76.9607,-76.947974,-76.93723,-76.9607,-76.947446,-76.947446,-76.947974,-76.947974,-76.941877,-76.957461,-76.93723,-76.941877,-76.941877,-76.957461,-76.941877,-76.947974,-76.9607,-76.9599,-76.9599,-76.988039,-76.994637,-76.994637,-76.9599,-76.994637,-76.985238,-76.994637,-76.988039,-76.9784,-76.990037,-76.988039,-76.9784,-76.990037,-76.9784,-76.952103,-76.952103,-76.9784,-76.952103,-76.9599,-76.990037,-76.952103,-76.9672,-76.9672,-76.9672,-76.9672,-76.985238,-76.985238,-76.985238,-76.971015,-76.971015,-76.971015,-76.971015,-76.988039,-76.990037,-77.02127,-77.017445,-77.02127,-77.02127,-77.017445,-77.02127,-77.0178,-77.0178,-77.0178,-77.017445,-77.032429,-77.017445,-77.0178,-77.032429,-77.032429,-77.032429,-76.987823,-76.987823,-76.987823,-76.987823,-76.999388,-76.999388,-76.999388,-76.999388,-77.03863,-77.038785,-77.038785,-77.038359,-77.0444,-77.043648,-77.043648,-77.04478,-77.044789,-77.03863,-77.043648,-77.041606,-77.041606,-77.043648,-77.038785,-77.038359,-77.038359,-77.038359,-77.044789,-77.044789,-77.04478,-77.04478,-77.04478,-77.0444,-77.038785,-77.03863,-77.0444,-77.041606,-77.044789,-77.03863,-77.0444,-77.041606,-77.046774,-77.053485,-77.053485,-77.048911,-77.048911,-77.046774,-77.048911,-77.053485,-77.047,-77.048911,-77.053485,-77.047,-77.047,-77.047,-77.046774,-77.046774,-77.045,-77.045,-77.045,-77.045],[81.2773031048644,17.5214154679352,67.8896162899747,47.2440472440709,56.1070405564221,57.7234787586472,73.1231837381278,49.7995983919549,81.65169930871,87.7211491032807,74.1822081094921,38.8844441904472,69.5629211577547,69.3181073024935,47.4447046571058,53.4696175411794,57.0526073023836,62.0564259364008,43.1508980207828,69.4982014155762,67.9117073853986,36.9052841744919,96.7677632272236,51.7590571784301,76.1839878189636,92.1303424502482,85.3639268075222,36.7151195013716,61.367743970265,61.5873363606513,80.3927857459859,54.7265931700485,83.3366666000027,59.5482997238376,85.8254041645013,99.6242942258564,85.615419172016,48.0104155366312,58.3780780773057,92.7685291464729,53.6749476012786,52.5357021462548,89.3308457365092,56.2672195865408,55.2630075185924,55.1361950083609,40.6693988153255,43.2087954009366,54.571054598569,86.8043777697876,64.4049687524185,71.6589143093865,48.1975103091436,29.034462281916,80.8517161227886,55.4616984954482,66.7308024828115,59.8163857149527,40.8778668719394,58.025856305616,66.7982035686589,41.8568990729127,53.1224999411737,36.9188298839495,58.7281874401041,65.3834841531101,83.2165848854662,60.4483250388297,38.4967531098403,55.9285258164383,57,31.4006369362152,45.2437841034545,51.0098029794274,89.6102672688794,45.1663591625449,43.8520238985614,41.8568990729127,40.7062648740952,32.218007387174,46.9254728266003,41.821047332653,45.0111097397076,59.6405902049938,37.0809924354783,53.2541078227774,57.6020832956587,68.7313611097583,37.6164857476081,42.6262829718942,63.6238948823475,31.3687742827162,65.4140657657052,50.8822169328342,81.3818161507839,61.5386057690617,32.5269119345812,73.6274405367999,49.2848861214064,42,78.8923316932641,69.4694177318336,72.9383301152419,23.1948270094864,38.742741255621,148.989932545793,97.7547952787995,47.1805044483418,38.5097390279394,131.78391404113,35.8608421540822,64.2261628933257,54.561891462815,70.2637886823647,68.847657912234,100.905896755343,47.8748368143433,45.1663591625449,58.2752091373339,144.100659262892,59.2283715798434,77.2398860693101,31.3049516849971,34.2490875790874,47.5394572960189,36.3318042491699,65.7571288910944,53.2447180478965,60.654760736483,68.6949779823824,79.435508432942,48.7339717240448,46.7118828565066,43.7721372564786,56.8418859644893,44.3508737230734,63.718129288296,40.024992192379,44.9666543118342,51.2249938994628,35.6370593624109,67.0447611674469,29.3598365118064,101.533245786787,98.1631295344642,43.7949768809164,74.1687265631546,52.4499761677734,34.3947670438397,48.9489530020817,76.8570100901668,54.9636243346452,55.6686626388671,46.6583325891528,41.1582312545134,25.8456959666402,46.2601340248815,50.5766744656072,49.0306026885251,49.0306026885251,56.2494444417009,69.7352134864446,14.6287388383278,68.2861625807162,85.3111950449646,71.8192174839019,44.8664685483491,72.7667506489056,36.5239647354993,43.6463056855904,73.8647412504776,42.1781934179263,62.5619692784682,49.8998997994986,55.4797260267208,35.9722114972099,62.4739945897491,49.8397431775084,36.9052841744919,47.3286382647969,55.145262715849,26.1916017074176,33.5410196624968,78.8035532193822,57.3323643328967,59.1861470278308,65.2763356814704,45.4312667664022,59.7829407105405,53.3197899470731,41.4004830889689,50.6754378372797,43.4971263418631,45.1220566907139,62.7295783502488,56.1693866799345,38.262252939418,47.4657771452233,56.7009700093393,59.4222180669823,85.7379729174885,49.5580467734555,71.7216843081644,82.6801064343775,27.2029410174709,88.357229472183,35.8608421540822,65.8862656401165,59.143892330485,40.0749298190278,70.221079456243,52.7825728815866,56.7978872846517,66.9925368977769,57.913728942281,66.1966766537415,75.2263251794211,64.6838465151849,42.9534631898291,72.2011080247388,75.4519714785505,43.2319326424346,71.9791636517124,42.2137418384109,69.108610172684,67.9485099174368,45.5741154604234,69.4478221400787,68.5638388656878,65.352888229978,68.629439747094,79.227520471109,86.0464990571958,73.7360156233031,67.8675180038286,41.9046536795139,59.7159945073345,44.4184646290256,45.7820925690384,60.1165534607565,48.3838816136118,115.468610453231,72.2772439983706,95.8957767578948,87.1951833532105,111.004504413109,59.9749947894954,113.881517376614,82.3468275041607,77.7817459305202,94.6625585963109,64.7765389628066,72.8628849277875,75.9012516365837,51.8266340793998,58.7111573723428,80.1623352953243,47.3180726572839,65.4293512118224,75.8551250740515,102.249694376071,97.9948978263665,88.6340792246414,95.2260468569393,86.6140866141299,111.233987611701,77.0973410695855,36.9323706252388,56.5420197729087,57.6367938039582,50.1996015920445,67.6091709755415,50.2593274925162,75.8221603490694,48.1040538832228,78.6002544525143,41.1217703899042,40.1995024844836,50.950956811428,60.613529842767,60.4814021001498,56.3116329012043,57.3323643328967,55.515763527128,42.6966040804184,27.2213151776324,35.2987251894456,51.4684369298311,38.7943294825416,70.5195008490559,70.0142842568572,34.2052627529741,63.3403504884525,43.9089968002003,49.8698305591667,49.9199358973947,75.3458691634784,56.5243310442503,67.1937497093294,80.6659779584925,34.2928563989645,48,51.254268114958,63.3719180710194,31.9061122670876,40.8044115262063,49.6588360717405,44.6542271235322,74.2361098118699,61.6035713250458,58.2408791142441,48.1144468948776,88.3628881374981,90.9560333347931,76.1839878189636,39.9374510954317,35.665109000254,75.6703376495705,64.2806347199528,44.3508737230734,23.5796522451032,35.9304884464434,77.3498545570708,43.0348695827,37.5499667110372,42.5205832509386,51.526692111953,66.7982035686589,29.8831055949679,57.9050947672137,42.8368999812078,50.438080851674,24.5560583156173,47.6969600708473,36.1801050302511,40.853396431631,31.3209195267317,45.7711699653832,50.2891638427206,21.9544984001002,39.6106046406767,46.7118828565066,48.6621002423858,60.0249947938357,87.1435597161374,91.1975876873944,106.282642044691,77.051930540383,103.995192196563,67.5351760196122,35.0142828000232,66.1286624694618,73.7631344236401,68.1615727518079,79.1264810287934,67.5351760196122,38.8715834511536,85.3111950449646,19.4935886896179,62.2012861603359,41.545156155682,57.0087712549569,68.0808343074613,90.8019823572151,78.2240372264178,63.4744042902334,91.0714005602198,105.066645516072,57.4020905542647,48.2700735445887,77.2204636090719,81.8718510844845,105.81115253129,50.0199960015992,74.0405294416511,64.3506021727847,53.9258750508511,78.9366834874635,52.8772162656091,93.1396800509858,99.8248466064436,70.1569668671615,86.191646927066,95.3729521405309,67.3869423553258,88.2609766544649,73.9053448676075,49.4064773081425,75.690157880665,77.8267306264371,78.4283112147648,78.2559901860554,60.9097693313642,87.6184911990614,60.4069532421558,28.5306852353742,52.2972274599715,47.0744091837593,83.7078252017098,77.7946013551069,68.60029154457,72,43.611924974713,23.4093998214393,86.5909926031571,77.3692445355388,82.975900115636,53.6376733276155,60.6959636219741,68.0661443009665,70.6186944087754,63.0158710167526,62.9841249839989,54.9181208709839,31.0966236109324,45.7820925690384,37.5099986670221,31.3687742827162,67.2458177138177,60.00833275471,56.7538544946508,44.0567815438214,74.8465096046569,76.9610290991486,52.2015325445527,34.1467421579277,53.5723809439155,21.6333076527839,42.9651021178817,39.8748040747538,26.2868788561898,32.8785644455472,28.7402157263998,33.0756708170825,28.0356915377524,42,27.6947648482525,18.0554700852678,17.7763888346312,38.6522961801754,28.6006992921502,23.5159520326097,25.2388589282479,24.4335834457412,22.2261107708929,13.6381816969859,36.6469644036174,27.0185121722126,20.0249843945008,23,32.2335229225724,23.473389188611,51.9230199429887,47.6655011512519,34.322004603461,12.4096736459909,28.3372546306095,45.4972526643093,48.3942145302514,34.6554469023269,53.9907399467724,38.9101529166874,42.1781934179263,20.591260281974,49.9699909945959,22.5831795812724,24.8596057893121,39,24.1246761636296,40.137264480779,39.3827373350304,33.466401061363,17.2046505340853,34.9571165858971,20.4939015319192,31.2569992161756,23.1948270094864,23.0867927612304,31.9687347262916,36.7151195013716,25.6320112359526,32.0936130717624,22.7376340018041,19.2093727122985,22.4053565024081,11.1803398874989,26.4575131106459,12.5698050899765,16.1554944214035,12.9228479833201,10.1488915650922,6.70820393249937,3.87298334620742,8.36660026534076,12.1243556529821,8.60232526704263,9.16515138991168,4.24264068711928,8.36660026534076,8,4.69041575982343,5.19615242270663,10.816653826392,8.54400374531753,4.58257569495584,6.2449979983984,5,11.7898261225516,6.08276253029822,3.3166247903554,2.23606797749979,3.74165738677394,6.32455532033676,1.73205080756888,7.68114574786861,6.48074069840786,12.2882057274445,20.2731349327133,19.2613602842582,3.60555127546399,20.4205778566621,17.1755640373177,21.540659228538,18.3030052177231,11.916375287813,13.8202749610853,15.4272486205415,12.0830459735946,14.247806848775,6.92820323027551,2.23606797749979,4.24264068711928,11.4017542509914,5.19615242270663,6.40312423743285,13.7840487520902,3.60555127546399,8.18535277187245,7.41619848709566,6.557438524302,9.4339811320566,18.6010752377383,13.6014705087354,18,11.4891252930761,7.21110255092798,10.0995049383621,9.79795897113271,18.2482875908947,13.7840487520902,44.9332838773219,75.953933407033,47.2440472440709,20.4450483002609,44.2153819388683,35.6370593624109,47.73887304912,67.1341939699882,81.0370285733627,73.0136973450872,141.908421173657,62.2012861603359,77.6595132614157,153.626169645669,102.464628043047,61.1800621117697,10.7238052947636,5,9.89949493661167,10.816653826392,8.06225774829855,7.48331477354788,4.58257569495584,8.88819441731559,87.3269717784832,73.348483283569,84.0535543567314,83.5523787812172,136.374484416991,53.4509120595711,43.1856457633784,52.3450093132096,55.4436651025164,58.4294446319662,61.2372435695795,48.8773976393997,69.4334213473598,62.5059997120276,59.39696961967,56.2583327161408,79.3032155716274,82.9939756849857,48.0520551069359,54.7813836992094,80.0062497558784,85.8836422143356,71.5891053163818,116.228223766863,81.4370922860093,84.3682404699778,81.2280739646091,73.5255057786072,36.9729630946723,75.8485332752058,131.02289876201,63.6710295189264,84.6640419540669,70.2851335632223,49.3558507170123,87.2696969170857,72.0832851637604,91.2523972287852,53.7866154354408,83.3606621854697,44.0567815438214,82.2313808712951,79.0316392339169,62.4019230472908,68.6075797561756,69.28924880528,58.591808301161,78.4346862045103,64.2417309853961,52.924474489597,61.5223536610881,42.3674403286297],null,null,{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"red","weight":1,"opacity":0.2,"fill":true,"fillColor":"red","fillOpacity":0.2,"dashArray":null},null]}],"limits":{"lat":[38.843222,38.956595],"lng":[-77.087171,-76.93723]}},"evals":[]}</script><!--/html_preserve-->


#Methods & Variable Selection
Since our analysis desired to understand attributes that increase usage trends of stations, we began with a base file that included aggregated number of rentals and mean duration based on station from the Capital City Bikeshare. The data set was also accompanied with geographic information (lat/long) variables for each station and surrounding features such as ATM, Cafe, etc. The total data set was 78 variables. We then reverse geocoded the lat/long variables with the Google API to get the associated zipcode of each station. Once we had the zipcode we loaded and merged local socioeconomic and demographic statistics at the zip level. In total, there were 83 before using pre-processing and subset algorithm techniques to reduce the number/complexity of the model. 

##Pre-processing
In order to reduce concerns of multicollinearity or correlated predictors, we removed all variables that had a correlation over 0.75. Additionally, we combined a number of like terms into broader buckets. For example, we created <i> retail </i> which was a composite of shop_art, shop_books, etc. Utilizing the `caret` package we also normalized and scaled our data to make better sense of our model. Essentially, this process makes it possible to compare on an 'on-average' basis of the predictors impact to the outcome (number of rentals), rather than the outcome variable value when other predictors = 0. 

##Variable and Model Selection 
Given the number of variables available to us and limited knowledge about what specifically drives rentals usage, we employed a number of  best subset variable selection algorithms to inform our selection of model features. The selection metric of measurement used for this analysis was the root-mean-squared-error (RMSE) or the average error of prediction when all model features are too at their average level. The result output and most important variables can be seen represented in graphs and tables within the appendix. 

<ol>
<li> Forward Regression </li>
<li> Hybrid Regression </li>
<li> Ridge Regression </li>
<li> Lasso Regression </li> 
</ol>

Upon running these algorithms, we find that a number of the most important features are consistent across methods, though the modelRidge produces the lowest RMSE on average. However, it is still quite elevated at 1942 -- meaning on average the error term prediction is off by that quantity when compared to actual results. The most significant predictors seem to be <i> tourism </i> as expected from our mapping. Finally, it is important to notice that despite our selection of variables being set to a max of 23, the feature importance drops rapidly after the top 10. Therefore, we will only use the top selected features in our final model. 

#Conclusion & Recommendations

Overall, tourism is the largest indicator of increased number of rentals per station. Based on this finding, it would benefit Pronto to not only include more stations/bikes in central tourist areas such as the Pike Place Market, but it may also benefit them to create a promotional strategy that targets tourists. This might include providing one-time discounted pricing for select hotels in the area to give away or perhaps increased marketing materials at major entry points (airport, ferry or via I-5 corridor). Fortunately, Seattle tourism figures have continued to increase and correspond closely to those of Washington D.C. (~20 million/year).

Secondarily, we find a strong negative correspondence to number of rentals based on increases in the unemployment rate. This may be indicative of commuting preference for those employed versus unemployed. An additional and surprising metric related to number of rentals per station is the percent of teen births. Though on the surface this may not make sense, it does have the potential to be a proxy for urban density, where those teens having births may be in more rural or suburban communities. 

The last series of features that are highly predictive of number of rentals are those that lie within other existing transportation infrastructure. For instance, we see that the railway subway entrance, traffic signals and bus stops all represent relationships to the number of rentals at a station. City ownership for Pronto may assist in leveraging transportation planning in a new way that elevates the usage of Pronto. For instance, participation in Sound Transit planning for future light rail stations or further integrated planning with Seattle may assist in driving rentals. 

Due to the RMSE remaining slightly elevated, more work can be done to attempt to drive this figure down by testing more outside data. For instance, it may be valuable to explore visitor statistics, transient nature of population as measured by total percent of population born in state (and presently living there), elevation topography (hills) or finding survey information measuring the number of bike owners in an area. Though both D.C. and Seattle populations are similar in size, it is important to understand how the geography and behaviors differ to get a read on how to install more stations and optimize the Pronto program further. 

#Appendix

##Full Model Results

<img src="001_Project_1_files/figure-html/distributionData-1.png" title="" alt="" style="display: block; margin: auto;" />






```r
#Full Model 
par(mfrow = c(2,2))
plot(model_full)
```

<img src="001_Project_1_files/figure-html/fullModelPlot-1.png" title="" alt="" style="display: block; margin: auto;" />

```r
#Graphical Analysis from full model
#[1] Residual v. Fitted: Heteroscedacity is present, as indicated by the "cone shape." This means the variability of a variable (num_rentals) is not constant across the range of values of a second variable(s) that predict it. Accuracy wanes in prediction of high volume rentals
#Source: http://www.statsmakemecry.com/smmctheblog/confusing-stats-terms-explained-heteroscedasticity-heteroske.html
#[2] Indicates leptokurtosis (high-kurtosis) or the distribution has "Fat-Tails". 
#Source: http://stats.stackexchange.com/questions/101274/how-to-interpret-a-qq-plot
#[4] Cooks Distance: How far the predicted value of your data points would move if your model were built without that data point included
#####Leverage: The impact on the OLS line of best fit (individually point impact)
```







###Forward Model:Cross-Validated(10); VarMax (25)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
![](001_Project_1_files/figure-html/modelForward-1.png)![](001_Project_1_files/figure-html/modelForward-2.png)

###Hybrid Model:Cross-Validated(10); VarMax (25)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
![](001_Project_1_files/figure-html/modelHybrid-1.png)![](001_Project_1_files/figure-html/modelHybrid-2.png)

###Ridge Model:Cross-Validated(10); Tune Length(10)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
![](001_Project_1_files/figure-html/modelRidge-1.png)![](001_Project_1_files/figure-html/modelRidge-2.png)

###Lasso Regression:Cross-Validated(10); Tune Lenth (10)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
![](001_Project_1_files/figure-html/modelLasso-1.png)![](001_Project_1_files/figure-html/modelLasso-2.png)

###Model Metric Comparison
<b><i>In-Sample</b></i><br>




```
## 
## Call:
## summary.resamples(object = results)
## 
## Models: forward, hybrid, ridge, lasso 
## Number of resamples: 10 
## 
## RMSE 
##         Min. 1st Qu. Median Mean 3rd Qu. Max. NA's
## forward 1704    1753   1927 2128    2307 3094    0
## hybrid  1639    1844   2021 2156    2502 3067    0
## ridge   1512    1636   1752 1942    2146 2788    0
## lasso   1510    1583   1790 1949    2214 2818    0
## 
## Rsquared 
##           Min. 1st Qu. Median   Mean 3rd Qu.   Max. NA's
## forward 0.4788  0.4940 0.5911 0.5823  0.6427 0.7429    0
## hybrid  0.3621  0.4711 0.5918 0.5582  0.6193 0.7113    0
## ridge   0.4571  0.6007 0.6416 0.6376  0.7276 0.7738    0
## lasso   0.4637  0.5673 0.6597 0.6305  0.7077 0.7623    0
```

<img src="001_Project_1_files/figure-html/compareModels-1.png" title="" alt="" style="display: block; margin: auto;" />

###Model Performance on Test Data

```
##   modelType TrainRMSE TestRMSE      diff
## 1   Forward  2127.863 1977.412 150.45121
## 2    Hybrid  2155.614 1976.436 179.17804
## 3     Ridge  1942.020 1897.543  44.47654
## 4     Lasso  1948.905 1854.540  94.36512
```

###R Packages Used


```r
sessionInfo()
```

```
## R version 3.2.3 (2015-12-10)
## Platform: x86_64-w64-mingw32/x64 (64-bit)
## Running under: Windows >= 8 x64 (build 9200)
## 
## locale:
## [1] LC_COLLATE=English_United States.1252 
## [2] LC_CTYPE=English_United States.1252   
## [3] LC_MONETARY=English_United States.1252
## [4] LC_NUMERIC=C                          
## [5] LC_TIME=English_United States.1252    
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
##  [1] leaps_2.9       rmarkdown_0.9.2 elasticnet_1.1  lars_1.2       
##  [5] car_2.1-1       MASS_7.3-45     caret_6.0-64    ggplot2_2.1.0  
##  [9] lattice_0.20-33 stringr_1.0.0   knitr_1.12.3    dplyr_0.4.3    
## [13] DT_0.1          leaflet_1.0.0  
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.4        compiler_3.2.3     formatR_1.2.1     
##  [4] nloptr_1.0.4       plyr_1.8.3         iterators_1.0.8   
##  [7] tools_3.2.3        digest_0.6.9       lme4_1.1-11       
## [10] jsonlite_0.9.19    evaluate_0.8       gtable_0.2.0      
## [13] nlme_3.1-124       mgcv_1.8-9         Matrix_1.2-3      
## [16] foreach_1.4.3      DBI_0.3.1          yaml_2.1.13       
## [19] parallel_3.2.3     SparseM_1.7        htmlwidgets_0.5   
## [22] MatrixModels_0.4-1 stats4_3.2.3       grid_3.2.3        
## [25] nnet_7.3-11        R6_2.1.2           minqa_1.2.4       
## [28] reshape2_1.4.1     magrittr_1.5       scales_0.4.0      
## [31] codetools_0.2-14   htmltools_0.3      splines_3.2.3     
## [34] assertthat_0.1     pbkrtest_0.4-6     colorspace_1.2-6  
## [37] quantreg_5.21      stringi_1.0-1      lazyeval_0.1.10   
## [40] munsell_0.4.3
```

```r
#render()
```