![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)


# MapmyIndia Place Search Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs. 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 17 November 2020 | MapmyIndia API Team ([KB](https://github.com/kunalbharti)) |


## SDK Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 17 November 2020 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

A simple plugin / widget to search for places powered by the best online maps from MapmyIndia. The Place Search plugin for MapmyIndia Web Map JS library is provided as a means to enable searching of Places on MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS library but it also possesses the adaptability to be used as an independent plugin within any web app implementation. Thus it enables developers to include MapmyIndia Places SDK in their own customized solutions easily.

The SDK offers the following basic functionalities: 
1. Ability to search for places directly with or without MapmyIndia Maps visual interface.
2. A MapmyIndia.search() method to initiate search across all types places available on MapmyIndia.
3. Ability to get information from MapmyIndia Place Search plugin through a callback
4. Include the Place Search Plugin with or without an interactive Map component.


## Live Demo

Visit the following link for visiting the live demo: 

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-search-plugin)

The above implementation uses MapmyIndia Interactive Map JS library as map rendering framework showcasing integration of Place Search plugin.

## Implementation

### Adding the MapmyIndia Place Search plugin script

#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

### 1. Initializing the Place Search plugin

#### Method

`MapmyIndia.search()`

```js
/*Search plugin initialization*/
            var placeOptions={
                location:[28.61, 77.23]/*,
                geolocation:true,
                pod:'City',
                bridge:true,
                tokenizeAddress:true,*
                filter:'cop:9QGXAM',
                distance:true,
                width:300,
                height:300*/
            };

new MapmyIndia.search(document.getElementById("auto"),placeOptions,callback);
```

#### Mandatory Parameters
1. `inputQuery`: The string which will be passed as input query to the search engine.

#### Optional Parameters
1. `Place Options`: Optional configurations for modifying the search request.
    - `location`: location coordinates which will be used as radial bias (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
    - `pod`: Place type which you want to restrict the results by. e.g. `pod:'city'`. Valid values are: 
        - SLC (sub locality)
        - LC (locality)
        - CITY
        - VLG (village)
        - SDIST (sub district)
        - DIST (district)
        - STATE
        - SSLC (sub sub locality)
    - `filter`: a parameter to restrict results by. e.g. `filter:'cop:9qgxam'`
        - Can be used to filter results by PIN code. e.g. `pin:110055`
        - Can be used to filter results by eLoc. e.g. `cop:9qgxam`
        - Can be used to filter results by view bound. e.g. `filter=bounds:28.598882,77.212407;28.467375,77.353513`
    - `bridge`: initiates a bridge to be created to provide applicable nearby API searches. Involves using Nearby Search Plugin in conjunction with Place Search Plugin.
    - `tokenizeAddress`: boolean value used to return address tokens from the searched places from MapmyIndia Search APIs. e.g. `tokenizeAddress:true`
    - `distance`: boolean value used to show aerial distance from location passed in `location`. of the searched place in results listing e.g. `distance:true`
    - `geolocation` : boolean value used to enable or disable current location selection . Default is true.
    - `width`: width of the suggested div. e.g. `width:300`
    - `height`: height of the suggested div. e.g `height:300`
2. `callback`: callback to get results/error after call or selection.

<br>

### 2. Calling MapmyIndia Place Search for programmatically fixed text

Following is an example of calling MapmyIndia.search() method programmatically for a fixed text rather than depending on a UI driven approach: 

```js
/*CALL for fix text - LIKE THIS*/
    new MapmyIndia.search("agra",placeOptions,callback);
```

### Sample code Snippet

```html
<html>
   <head>
      <title>MapmyIndia Plugin - Search Plugin</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta name="desciption" content="Mapmyindia Search Plugin">
      <script src="https://apis.mapmyindia.com/advancedmaps/v1/<token/key>/map_load?v=1.3"></script>
      <script src="https://apis.mapmyindia.com/advancedmaps/api/<token/jwt key>/map_sdk_plugins"></script>
      <style>
         body{margin: 0}
         #map{
         width: 100%; height: 100vh;margin:0;padding: 0;
         }
         .infoCls_map{margin-top: 60px !important;min-width: 300px}
         #auto{color: #000;max-width: 99%;width:300px;position:absolute;z-index: 999;font-size: 15px;padding:10px;border: 1px solid #ddd;outline: none !important;top:5px;border-radius:10px;margin:4px;}
      </style>
   </head>
   <body>
      <div id="map"></div>
      <input  type="text" id="auto" name="auto" class="search-outer form-control as-input" placeholder="Search places or eLoc's..." required="" spellcheck="false" >
      <script>
         /*Map Initialization*/
          var map = new MapmyIndia.Map('map', {center: [28.09, 78.3], zoom: 5, search: false});
          
          /*Search plugin initialization*/
            var optional_config={
                location:[28.61, 77.23],
               /* pod:'City',
                bridge:true,
                tokenizeAddress:true,*
                filter:'cop:9QGXAM',
                distance:true,
                width:300,
                height:300*/
            };
            new MapmyIndia.search(document.getElementById("auto"),optional_config,callback);
            
            /*CALL for fix text - LIKE THIS
             * 
             new MapmyIndia.search("agra",optional_config,callback);
             * 
             * */
         
            var marker;
            function callback(data) { 
                if(data)
                {
                    var dt=data[0];
                    if(!dt) return false;
                    var eloc=dt.eLoc;
                    var place=dt.placeName+", "+dt.placeAddress;
                    /*Use elocMarker Plugin to add marker*/
                    if(marker) marker.remove();
                    marker=new MapmyIndia.elocMarker({map:map,eloc:eloc,popupHtml:place,popupOptions:{openPopup:true}}).fitbounds();
                }
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
