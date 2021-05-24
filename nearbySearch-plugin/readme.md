![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)


# MapmyIndia Nearby Search Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs. 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 14 January 2021 | MapmyIndia API Team ([KB](https://github.com/kunalbharti)) |


## SDK Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 14 January 2021 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

A simple plugin / widget to search for nearby places powered by the best online maps from MapmyIndia. The Nearby Search plugin for MapmyIndia Web Map JS library is provided as a means to enable radially searching for Nearby Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to search for nearby places directly with or without MapmyIndia Maps visual interface.
2. A MapmyIndia.nearby() method to initiate nearby search across all categories of places available on MapmyIndia.
3. Ability to get information from MapmyIndia Place Search plugin through a callback
4. Include the Nearby Search Plugin with or without an interactive Map component.


## Live Demo

Visit the following link for visiting the live demo: 

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-nearby-plugin)

The above implementation uses MapmyIndia Interactive Map JS library as map rendering framework showcasing integration of Place Search plugin.

## Implementation

### Adding the MapmyIndia Place Search plugin script

#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

### 1. Initializing the Nearby Search plugin

#### Method

`MapmyIndia.nearby()`

```js
/*Nearby plugin initialization*/
var options = {
  divId: 'nearby_search',
  map: map,
  keywords: 'atm',
  refLocation: [28.632735, 77.219696],
  fitbounds: true,
  geolocation: true,
  click_callback: function(d) {
    alert(d);
  }
}

var nr = MapmyIndia.nearby(options);
```

#### Mandatory Parameters
1. `keywords`: The string or JSON object which will be passed as input query to the search engine. Examples
    - **As a string**: `keywords:"atm"`
    - **As a JSON object**: `keywords:{'FINATM':'ATMS','FODCOF':'Restaurants'}`
    <br>This mechanism is used to display a selection of POI categories on a UI.
    <br>If `keywords` parameter is used, then `refLocation` input also becomes mandatory.

OR

1. `hyperLink`: This is the URL received from MapmyIndia Place Search plugin for bridged Nearby Search. i.e. A Nearby Search trigerred directly from the Place Search Plugin.

#### Optional Parameters
1. `refLocation`: location coordinates which will be used as centroid of the radial search reference . e.g. `refLocation:[28.61, 77.23]` OR `refLocation:[28.61, 77.23]`
2. `map`: A map object from our Maps SDK. Markers can also be passed here that will be displayed on map. Custom icons also can be passed here.
3. `divId`: The HTML where developer wishes results to be displayed.
<br>Example: `divId:document.getElementbyId('Nrdiv');`
4. `divHeight`: (in pixels) for customizing or improving results display UI.
5. `icon`: (object) To set the icons of the resulting categories of results.
    - *Single Category*: Example: 
        ```js
        icon: {
            url: '2.png'
        }
        ```
        OR 
         ```js
         icon: {
            html: " < div > < img src = 'pin.png' > < /div>",
            width: 30,
            height: 40
        }
        ```
    - *Multiple Category*: Example: 
        ```js
        icon: {
            'FINATM': {
                url: 'atm.png',
                height: 40,
                width: 30
            },
            'FODCOF': {
                url: 'food.png',
                height: 40,
                width: 32
            }
        }
        ```
        Optional parameters for icon configuration are as follows:
        - `offset`: Example: `offset:[20,40]`
        - `popupAnchor`: Example: `popupAnchor:[-10,20]`
6. `popup`: (boolean) Default is true if map is used. Used to bind popup to markers.
7. `popupOptions`: (object) Used to define pop up optional configuration. <br>Example: `popupOptions: {maxWidth:250}`
8. `fitbounds`: (boolean) Default is true. Used to fit all markers to in map view bound.
9. `geolocation`: boolean value used to enable or disable current location selection . Default is true.
10. `radius`: (number): Defines the radius of nearby search.
11. `bounds`: (geographic bounds): Used to define the rectangular bounds within which nearby search will work.
12. `sortBy`: (string)Used to sort the nearby search results.
13. `page`: (number): to request another page of results if available.
14. `pod`: (string): to filter to a certain type of results.
15. `callback`: (method): results will be returned in this method if specified.
16. `callback_click`: (method): a method that will be called when user clicks on any listing. The action returns the eLoc of the selected place.

<br>

### Types of Nearby Search Implementations

#### 1. Get data from category & coordinates

Following is an example of calling MapmyIndia.nearby() method to get data from category and coordinates: 

```js
var res=MapmyIndia.nearby({keywords:"atm",refLocation:"123ZRR"});
```

#### 2. Get data from MapmyIndia Search category url

```js
var res=MapmyIndia.nearby({hyperLink:'https://atlas.mapmyindia.com/api/places/nearby/json?explain&richData&&refLocation=28.61,77.23&keywords=FINATM'});
```

#### 3. Get data from category & location selection UI

```js
var res=MapmyIndia.nearby({divId:'nearby_divId',keywords:{'FINATM':'ATMs', 'FODCOF':'Restaurants'}});
```
This will place a selection of keywords and a location selection UI inside `divId`.

### Remove Nearby Markers from Map

Use remove() method to remove markers from map.

```js
var markers=res.markers();
markers.remove();
```

### Add Event to Markers

Use addListener() method to associate events to markers.

```js
markers.addListener('click',function(data){ console.log(data);});
```

### Sample Code Snippet

```html
<html>
   <head>
      <title>MapmyIndia Plugin - Nearby Plugin</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="desciption" content="Mapmyindia Nearby Plugin">
      <script src="https://apis.mapmyindia.com/advancedmaps/v1/<token>/map_load?v=1.5"></script>
      <script src="https://apis.mapmyindia.com/advancedmaps/api/<token>/map_sdk_plugins"></script>
      <style>
         body{margin: 0}
         #map{
         width: 99%; height: 300px;margin:0;padding: 0;
         }
      </style>
   </head>
   <body>
      <div id="nearby_search" style=" margin: 5px;width:99%;height:250px;overflow-y: auto;border-radius: 10px;"></div>
      <div id="map"></div>
      <script>
         /*Map Initialization*/
          var map = new MapmyIndia.Map('map', {center: [28.09, 78.3], zoom: 5, search: false});
         
          /*Nearby plugin initialization*/
            var options={
                    divId:'nearby_search',
                    map:map,
                    keywords:'atm',
                    refLocation:[28.632735,77.219696],
                    fitbounds:true,
                    click_callback:function(d){alert(d);}
            }
         
             var nr=MapmyIndia.nearby(options); 
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
