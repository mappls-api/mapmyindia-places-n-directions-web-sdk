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
        icon: {
            url: '2.png',
            width: 30, //optional
            height: 40 //optional
        }
        ```
        OR 
         ```js
         icon: {
            html: " < div > < img src = 'pin.png' > < /div>",
            width: 30, //optional
            height: 40, //optional
            offset:[20,40] //optional

        }
        ```
   
12. `end icon` (string) : To set the icon for end point.
6. `via`: (object) : To add a geo positions between start and end points.
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
14. `fitbounds`: (boolean). Used to fit the route to in map view bound. Default is true.
15. `search` : Referred to the intergarated MapmyIndia Search. Default remains true.
16. `divId`: The HTML where developer wishes results to be displayed.
17. `divWidth`: (in pixels) For customizing or improving results display UI.
18. `autoSubmit` : Property that will be called when user directly want to display the results. Default remains true.
19. `geolocation`: boolean value used to enable or disable current location selection . Default is true.
20. `maxVia`: Property that helps to limit the number of viapoints in any route. maximum Value  up to 98.


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
