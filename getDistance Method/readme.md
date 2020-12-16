![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)
# MapmyIndia getDistance Method for MapmyIndia Map JS WEB SDK

**Easy To Integrate Distance Matrix APIs & Map SDKs For Web Applications**

Powered with India's most comprehensive and robust mapping functionalities. Now Available for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development.
2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs.

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 15 December 2020 | MapmyIndia API Team ([MH](https://github.com/mishkat313)) |


## Method Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 15 December 2020 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

This method, offered by MapmyIndia Places & Directions SDK for Web, computes the routable distance and duration between a set of source/primary positions and a list of all supplied secondary positions using two mode of route calculation i.e. optimal OR shortest. The method also takes into account different modes of transport like 4 wheelers, two wheelers + more. Please note that maximum number of points are limited to 100 only including source and secondary positions.

The method offers the following basic functionalities: 
1. The method computes the distance and duration from origin to number of supplied destinations on maps.
2. The ability to set the vehicle profile like driving, biking and trucking.
3. Easily set the resource for traffic and ETA information.
4. The method also has 'many to many' functionality in case of multiple origins and destinations.
5. It allows to use origin and destinations in MapmyIndia's digital address (semicolon separated) eLoc or WGS 84 geographical coordinates both.
6. This method can only be used when **`CORS`** is enabled on your project. For details, please contact apisupport@mapmyindia.com.

## Live Demo

Visit the following link for visiting the live demo:

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia-maps-distance-matrix-plugin)

## Implementation
#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

## Method

`MapmyIndia.getDistance()`

## Properties
### Mandatory

1. `coordinates `(string): Semicolon separated eloc or lat,long or both.
2. `callback`: Method to get response
### Optional
1. `resource` (string): Default is `distance_matrix` and can be changed to `distance_matrix_eta` or `distance_matrix_traffic` as per requirement.
2. `profile` (string): Default `driving` for four wheelers and can be changed to `biking` and `trucking` for two wheelers and heavy vehicles respectively.
3. `rtype` (boolean): type of route required for navigation, where values mean:
-   `0` optimal (default) 
-   `1` shortest (it will calculate route by excluding access penalties like private roads, etc.)

4. `region` (string): It is for the available countries. Default is India; for other countries (Sri Lanka, Nepal, Bangladesh & Bhutan) this parameter is mandatory. Possible values are `ind` (for India, default), `lka` (for Sri Lanka) , `npl` (for Nepal) , `bgd` (for Bangladesh), `mmr` (for Myanmar) and `btn` (for Bhutan).

5. `sources` (string): To specify which of the coordinates/eLoc supplied are to be treated as *source* position for 'many to many' distance matrix calculation. The input is indicative of that coordinate/eLoc's index.
E.g. 0;1 means that 0th and 1st pairs are source points. Default value is 0. The indexes must be semi-colon separated. e.g: 0;1;2;...
6. `destinations` (string): To specify which of the coordinates/eLoc supplied in the method are to be treated as destination position for 'many to many' distance matrix calculation. The input is indicative of that coordinate/eLoc's index. 
E.g. 2;3 means that 0th and 1st pairs are destination points. Default value is all. The indexes must be comma separated. e.g: 3;4;5;...

## Example
```js
MapmyIndia.getDistance({
    coordinates: "mmi000;123zrr",
    callback: function(data) {
        console.log(data);
    }
});
```

### Sample code Snippet

```js
/*CALLING DISTANCE*/
MapmyIndia.getDistance({
    coordinates: "518NSV;123ZRR;28.9797,77.6763"
}, function(data) {
    resdiv.innerHTML = JSON.stringify(data).replace(/{/g, '<br>{<br>').replace(/}/g, '<br>}<br>').replace(/","/g, '",<br>"');
});
```




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