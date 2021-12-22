![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)

# MapmyIndia Directions Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Routing APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Document Version History

| Version | Last Updated  | Author                                                        |
| ------- | ------------- | ------------------------------------------------------------- |
| 0.0.1   | 04 March 2021 | MapmyIndia API Team ([MS](https://github.com/mamtasharma117)) |

## Introduction

This plugin, offered by MapmyIndia Places & Directions SDK for Web, uses integrated places searches for directions for several modes of transportation, including driving, biking and walking.

The plugin offers the following basic functionalities:

1. Takes support of MapmyIndia Place search for searching locations of origin, destinations and via points.
2. It allows to use origin and destinations in MapmyIndia's digital address (semicolon separated) eLoc or WGS 84 geographical coordinates both.
3.  The ability to set the vehicle profile like driving, and biking.
4. Easily set the resource for traffic and ETA information.


For details, please contact apisupport@mapmyindia.com.

## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-direction-plugin)

## Implementation


### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

## Method

`MapmyIndia.direction()`

## Properties

### Mandatory

  1.  map(object): vector map or raster map object from respective MapmyIndia Map SDKs.

## Example

```js
MapmyIndia.direction({map:map,start:"28.545,77.545",end:{label:'India Gate, Delhi',geoposition:"1T182A"}});
```
## Additional Parameter - alongTheRoute 
 
1. `alongTheRoute` : _true/false_. Default is false.
    
    To access this parameter , please contact [API Support](mailto:apisupport@mapmyindia.com)
    This parameter takes the encoded route along which POIs will be searched. 
    
    This parameter is further having many configurable options listed below.

    - `buffer`: 200, _// Buffer of the road. Minimum value is 25m, maximum is 1000m and default is 25m_
    - `sort`: false, _//default is true_
    - `category`:  
        - `catCode`: 'FINATM', _//The POI category code to be searched. Only one category input supported by default_
        - `icon`: "icon image path
        " _//absolute path of the desired image_
        - `width`:  '30px' _//width of the icon image_
        - `height`: '30px' _//height of the icon image_
        - `label`: 'Restaurants' _the name  user puts to show the category. For Eg: "Restaurants"_

    - `page`: 1,  _// Used for pagination, Default is 1_
    - `poicallback`: to get data of alongtheroute pois.

 Refer to the Code Snippet if the you need to configure the default options.
 
 ```js
        alongTheRoute: {
                          options: { "page": 1, "buffer": 1000, "sort": false },
                          category: [
                              { catCode: 'FINATM', icon: "custom icon url", width: '30px', height: '30px',label:'ATM' },
                              { catCode: 'HOTALL', icon: "custom icon url", width: '30px', height: '30px',label:'Hotels' }
                          ],
                          poicallback: function (data) { console.log(data); }
                      }
 ```
 
 _*Advisory - Route length not more than 30 kms long_


### Optional Parameters

1. `start` (string): Eloc or lat,long.
2. `end` (string): Eloc or lat,long.
3. `resource` (string): Default is `route_adv` and can be changed to `route_eta` or `route_traffic` as per requirement.
4. `profile` (string): Default `driving` for four wheelers and can be changed to `biking` and `trucking` for two wheelers and heavy vehicles respectively.
5. `rtype` (boolean): type of route required for navigation, where values mean:

   - `0` optimal (default)
   - `1` shortest (it will calculate route by excluding access penalties like private roads, etc.)

6. `bearings`(integer): Limits the search to segments with given bearing in degrees. The referencing will be to the true north and in clockwise direction. (shall be part of premium offering)
7.  `alternatives`: Search for alternative routes. Passing a number: e.g. alternatives=n searches for up to n alternative routes. Please note that even if alternative routes are requested, a result cannot be guaranteed.
6.  `radiuses`: Limits the search to given radius in meters. For all way-points including start and end points. {radius};{radius}[;{radius} ...]. (shall be part of premium offering).
7. `steps`(boolean): Return route steps for each route leg. Possible values are true/false. By default it will be used as true. <Recommended=false; unless otherwise recommended by MapmyIndia>
7.  `exclude`(string): Additive list of road classes to avoid, order does not matter. Possible values are toll, motorway & ferry. Multiple values can be selected.
8. `start_icon` (string): To set the icon for start point.
    - Example: 
        ```js
        start_icon: {
            url: '2.png',
            width: 30, //optional
            height: 40 //optional
        }
        ```
        OR 
         ```js
         start_icon: {
            html: " < div > < img src = 'pin.png' > < /div>",
            width: 30, //optional
            height: 40, //optional
            offset:[20,40] //optional

        }
        ```
   
12. `end icon` (string) : To set the icon for end point.
13. `via`: (object) : To add a geo positions between start and end points.
   - Example: For single via Point
        ```js
        via: {
            label: 'mathura', //optional
            geoposition: "28.544, 77.4541"
        }
        ```
   - Example: For multiple via Points, user must pass the via points as array
        ```js
        via:[{label:'mathura',geoposition:"28.544,77.4541"},{label:'Koshi',geoposition:"28.144,77.4541"}],
        ```
14. `via_icon` (object): To set the icon for via points,
     - Example: via_icon:{url:'1.png',width:20,height:40} 
      or via_icon:{html: < div > < img src = 'pin.png' > 1< /div>,width:20,height:40}.
15. `fitbounds`: (boolean). Used to fit the route to in map view bound. Default is true.
16. `search` : Referred to the intergarated MapmyIndia Search. Default remains true.
17. `divId`: The HTML where developer wishes results to be displayed.
18. `divWidth`: (in pixels) For customizing or improving results display UI.
19. `autoSubmit` : Property that will be called when user directly want to display the results. Default remains true.
20. `geolocation`: boolean value used to enable or disable current location selection . Default is true.
21. `maxVia`: Property that helps to limit the number of viapoints in any route. maximum Value  up to 98.
22. `searchChars` : number of characters required to start search. ie searchChars:2
23. `pod`: Place type which you want to restrict the results by. e.g. `pod:'city'`. Valid values are: 
        - SLC (sub locality)
        - LC (locality)
        - CITY
        - VLG (village)
        - SDIST (sub district)
        - DIST (district)
        - STATE
        - SSLC (sub sub locality)
        - POI (place of interest)
24 `distance`: boolean value used to show aerial distance from location passed in `location`. of the searched place in results listing e.g. `distance:true`
25 `hyperLocal`: This parameter lets the search give results that are hyper-localized to the reference location passed in the location parameter. This means that nearby results are given higher ranking than results far from the reference location. Highly prominent results will still appear in the search results, however they will be lower in the list of results. This parameter will work ONLY in conjunction with the location parameter.
26 `location`: location coordinates which will be used as radial bias search (not restriction; only BIAS). e.g. `location:[28.61, 77.23]`
27. callback: (function). to get callback data after route plotted.



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
