![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)


# MapmyIndia Place Details Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs. 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 03 October 2020 | MapmyIndia API Team ([KB](https://github.com/kunalbharti)) |


## SDK Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 03 October 2020 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

A simple plugin / widget to render details of a particular place. The Place Details plugin for MapmyIndia Web Map JS library is provided as a means to enable rendering of MapmyIndia Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web map implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to render places directly on map with reference to the provided eLoc(s).
2. A getELoc() method to fetch the details of a place.
3. Customizable markers
4. Remove said markers from map.


## Live Demo

Visit the following link for visiting the live demo: 

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-geteloc-plugin)

The above implementation uses MapmyIndia Interactive Map JS library as map rendering framework showcasing integration of Place Details plugin.

## Implementation

### Adding the MapmyIndia Place Details plugin script

#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

### 1. Initializing the Place Details plugin

#### Method

`MapmyIndia.getEloc()`

```js
var elocObj = MapmyIndia.getEloc({ map: map, eloc: '3F45CB', callback: elocData });
```

#### Mandatory Parameters
1. `eLoc`: The eLoc whose details are required.

#### Optional Parameters
1. `map`: Map Object
2. `icon`: MapmyIndia Interactive Map JS icon object 
    (leaflet compatible icon object).
    - example: 
        ```js
        L.icon({iconUrl: 'https://maps.mapmyindia.com/images/general.png'});
        ```
3. `divId`: The div to put the result in.
4. `callback`: to return data to a specified callback method.
5. `preserve` : To preserve multiple markers on subsequent rendering of new eLoc(s).
6. `markerPopup` (boolean): to show pop-ups on marker click. Default is true.(example: `markerPopup:true`)
7. `fitbounds` (boolean): To show all rendered eLoc(s) in a single view bound. (example: `fitbounds:true`)
8. `padding` : padding in fitbounds, if any. (Example: `padding:[10,10]`)
9. `infoDiv` (boolean): To render html div on map or not. Default is true. (example: `infoDiv:true`)
10. `click_callback`: method to call on click of callback. 

<br>

### 2. Removing the Markers populated by Place Details plugin

```js
elocObj.remove();
```
<br>

### 3. Setting up the div content for populating details from getEloc()

```js
elocObj.setDivContent(“Div html);
```

### Sample code Snippet

```html
<html>
<head>
    <title>MapmyIndia Plugin - getEloc Plugin</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="desciption" content="Mapmyindia getEloc Plugin">
    <script
        src="https://apis.mapmyindia.com/advancedmaps/v1/0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6/map_load?v=1.5"></script>
    <script
        src="https://apis.mapmyindia.com/advancedmaps/api/0XXXXXXf-dXX0-4XX0-8XXa-eXXXXXXXXXX6/map_sdk_plugins"></script>
    <link rel="icon" href="https://www.mapmyindia.com/images/favicon.ico" type="image/x-icon">
    <style>
        #map {
            width: 100%;
            height: 60vh;
        }
    </style>
</head>

<body>
    <div id="map"></div>
    <script>
    /*Map Initialization*/
        var map = new MapmyIndia.Map('map', { center: [28.09, 78.3], zoom: 5, search: false, zoomControl: true, location: false, fullscreen: true, traffic: false, scrollWheelZoom: false });
    /*getEloc plugin initialization*/
        this.mk = MapmyIndia.getEloc({ map: map, eloc: '3F45CB', callback: elocData }); 
        function elocData(data) 
            { 
                console.log(data); 
            }
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
