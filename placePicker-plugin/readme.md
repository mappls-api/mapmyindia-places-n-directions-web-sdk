![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)


# MapmyIndia Place Picker Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs. 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 09 December 2020 | MapmyIndia API Team ([KB](https://github.com/kunalbharti)) |


## SDK Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 09 December 2020 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

A simple plugin / widget to pick places from the map. This SDK also has integrated Place Picker Plugin as optional component that enables one to narrow down to picked place by searching for it first and then changing the position of the resulting point on map to fine-tune the results.

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to pick or search places directly with or without MapmyIndia Maps visual interface.
2. A MapmyIndia.placePicker() method to initiate the plugin and pick places from MapmyIndia Maps.
3. Ability to get information from MapmyIndia Place Picker plugin through a callback.
4. Include the Place Picker Plugin with or without an interactive Map component.


## Live Demo

Visit the following link for visiting the live demo: 

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-place-picker)

The above implementation uses MapmyIndia Interactive Map JS library as map rendering framework showcasing integration of Place Picker plugin.

## Implementation

### Adding the MapmyIndia Place Picker plugin script

#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

### 1. Initializing the Place Picker plugin

#### Method

`MapmyIndia.placePickersearch()`

```js
/*Place Picker plugin initialization*/
var options=
    {
        map:map,
        callback:callback_method
        /*
        location:{lat:28.8787,lng:77.08888}, //to open that location on map on initailization
        closeBtn:true,
	geolocation:false,
        closeBtn_callback:closeBtn_callback,
        search:true,
        topText:'Location Search',
        pinImage:'pin.png', //custom pin image
        pinHeight:40
        */
    };
var picker = new MapmyIndia.placePicker(options);
```

#### Mandatory Parameters
1. `Place Options`: any object containing any of the two following mandatory configurations values.
    - `map`: object > vector map or raster map object from respective MapmyIndia Map SDKs
    ##### OR
    - `location`: (lat,lng) object // to get data without map.

#### Optional Parameters
1. `Place Options`: any object containing optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `geolocation`: boolean value used to enable or disable current location selection . Default is true.
    - `closeBtn`: (boolean): to give the option to close Place Picker (including hiding the top bar that has search & lower bar area that has the 'Done' button and related sub-text). Default is `true`.
    - `closeBtn_callback`: A callback method that is called when user clicks on the close button at the top left. To provide a call to action upon user closing the Place Picker plugin and thus providing the ability to continue towards further action by the consuming app.
    - `search`: (boolean): To enable / disable the integrated Place Search plugin. Default is `true`.
    - `topText`: The banner text to show at the top as title of the Place Picker plugin. Default is `Place Picker`.
    - `pinImage`: (URL) The PIN icon on the map. 
    - `pinHeight`: (number). To adjust the placement of the PIN icon on the map.
    - `callback`: (method): to get data after location selection . If no callback method is specified, UI `GET` button will be hidden. In this case, the consuming app can get data by calling method `getData()`.

<br>

### 2. Calling MapmyIndia Place Picker for programmatically fixed text

Following is an example of calling MapmyIndia.placePicker() method programmatically for a fixed pair of coordinates rather than depending on a UI driven approach: 

```js
/*CALL for coordinates - LIKE THIS*/
    var obj=MapmyIndia.placePicker({location:{lat:28.9898,lng:77.9898}});
```

### 3. Method for removing place picker plugin from map
#### Method
`remove()`

```js
obj.remove();
```

### 4. Method for programmatically setting location on map.
#### Method
`setLocation()`

```js
obj.setLocation({lat:28.42424,lng:77.232323});
```

### 5. Method for getting location data from Place Picker plugin.

#### Description
This method is especially useful if no callback is given in options.
As per the current status of the Place Picker plugin's UI (map view and placement of PIN on map), the location data is returned.

#### Method
`getLocation()`

```js
obj.getLocation();
```


### Response Structure of Place Picker Data

```json
{	
    area: "India", //country information
	city: "New Delhi", // city of the pinned place.
	district: "South East Delhi District", // district of the pinned place.
	formatted_address: "Industrial Estate Phase 1, New Delhi, Delhi, India", // complete formatted address of the pinned place.
    houseName: "Equalisatcon Pump House", // house name of the pinned place.
    houseNumber: "", // house number of the pinned place.
	lat: "28.5237002235929", // latitude of the pinned place as per input coordinates.
	lng: "77.28024601936342", // longitude of the pinned place as per input coordinates.
	locality: "Okhla Industrial Estate Phase 1", // locality number of the pinned place.
	pincode: "110020", // PIN of the pinned place.
	poi: "BSES", // POI reference for the pinned place.
	poi_dist: "78", // Referenced POI's distance from the pinned place.
	responsecode: 200, // Response code of the Place Plugin
	state: "Delhi", // state of the pinned place.
	street: "Unnamed Road", // Street reference for the pinned place.
	street_dist: "16", // Referenced street's distance from the pinned place.
	subDistrict: "Kalkaji", // subdistrict of the pinned place.
	subLocality: "Block C", // sublocality of the pinned place.
	subSubLocality: "", // subsublocality of the pinned place.
	village: "" // village of the pinned place.
}

```

### Sample code Snippet

```html
<html>
   <head>
      <title>MapmyIndia Plugin - Place Picker</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="desciption" content="Mapmyindia Place Picker Plugin">
      <script src="https://apis.mapmyindia.com/advancedmaps/v1/<token/key>/map_load?v=1.3"></script>
      <script src="https://apis.mapmyindia.com/advancedmaps/api/<token/jwt key>/map_sdk_plugins"></script>
      <style>
         body{margin: 0}
         #map{
         width: 100%; height: 100vh;margin:0;padding: 0;
         }
      </style>
   </head>
   <body>
      <div id="map"></div>
      <script>
         /*Map Initialization*/
          var map = new MapmyIndia.Map('map', {center: [28.62, 77.09], zoom: 15, search: false});
          
          /*Place Picker plugin initialization*/
           var options={
                map:map,
                callback:callback_method
               /*
                location:{lat:28.8787,lng:77.08888},//to open that location on map on initailization
                closeBtn:true,
                closeBtn_callback:closeBtn_callback,
                search:true,
                topText:'Location Search',
                pinImage:'pin.png', //custom pin image
                pinHeight:40
                */
            };
            var picker= new MapmyIndia.placePicker(options);
            function callback_method(data) {
                console.log(data);alert(JSON.stringify(data));
             }   
             /*methods
              * 
              picker.remove();
              picker.getLocation();
              picker.setLocation({lat:28.8787,lng:77.787877});
              * 
              */
      </script>
   </body>
</html>
```

<br>

That's All !


For any queries and support, please contact: 

[<img src="https://www.mapmyindia.com/images/logo.png" height="40"/> </p>](https://www.mapmyindia.com/api)
Email us at [apisupport@mapmyindia.com](mailto:apisupport@mapmyindia.com)


![](https://www.mapmyindia.com/api/img/icons/support.png)
[Support](https://www.mapmyindia.com/api/index.php#f_cont)
Need support? contact us!

<br></br>

[<p align="center"> <img src="https://www.mapmyindia.com/api/img/icons/stack-overflow.png"/> ](https://stackoverflow.com/questions/tagged/mapmyindia-api)[![](https://www.mapmyindia.com/api/img/icons/blog.png)](http://www.mapmyindia.com/blog/)[![](https://www.mapmyindia.com/api/img/icons/gethub.png)](https://github.com/MapmyIndia)[<img src="https://mmi-api-team.s3.ap-south-1.amazonaws.com/API-Team/npm-logo.one-third%5B1%5D.png" height="40"/> </p>](https://www.npmjs.com/org/mapmyindia) 



[<p align="center"> <img src="https://www.mapmyindia.com/june-newsletter/icon4.png"/> ](https://www.facebook.com/MapmyIndia)[![](https://www.mapmyindia.com/june-newsletter/icon2.png)](https://twitter.com/MapmyIndia)[![](https://www.mapmyindia.com/newsletter/2017/aug/llinkedin.png)](https://www.linkedin.com/company/mapmyindia)[![](https://www.mapmyindia.com/june-newsletter/icon3.png)](https://www.youtube.com/user/MapmyIndia/)




<div align="center">@ Copyright 2020 CE Info Systems Pvt. Ltd. All Rights Reserved.</div>

<div align="center"> <a href="https://www.mapmyindia.com/api/terms-&-conditions">Terms & Conditions</a> | <a href="https://www.mapmyindia.com/about/privacy-policy">Privacy Policy</a> | <a href="https://www.mapmyindia.com/pdf/mapmyIndia-sustainability-policy-healt-labour-rules-supplir-sustainability.pdf">Supplier Sustainability Policy</a> | <a href="https://www.mapmyindia.com/pdf/Health-Safety-Management.pdf">Health & Safety Policy</a> | <a href="https://www.mapmyindia.com/pdf/Environment-Sustainability-Policy-CSR-Report.pdf">Environmental Policy & CSR Report</a>

<div align="center">Customer Care: +91-9999333223</div>
