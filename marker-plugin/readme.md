![MapmyIndia APIs](https://www.mapmyindia.com/api/img/mapmyindia-api.png)


# MapmyIndia Marker Plugin for MapmyIndia Map JS WEB SDK

**Easy To Integrate Maps & Location APIs & SDKs For Web & Mobile Applications**

Powered with India's most comprehensive and robust mapping functionalities.
**Now Available**  for Srilanka, Nepal, Bhutan, Bangladesh and Myanmar.

1. Copy and paste the JWT API key or generated Auth token from your API keys available in the dashboard (http://www.mapmyindia.com/api/dashboard) in the sample code for interactive map development. 

2. The sample code is provided to help you understand the very basic functionality of MapmyIndia APIs. 

## Document Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 20 November 2020 | MapmyIndia API Team ([KB](https://github.com/kunalbharti)) |


## SDK Version History

| Version | Last Updated | Author |
| ---- | ---- | ---- |
| 0.0.1 | 20 November 2020 | MapmyIndia API Team ([BP](https://github.com/balmukandpathak)) |

## Introduction

A simple plugin to render places on map as markers. The Marker plugin for MapmyIndia Web Map JS library is provided as a means to enable rendering of searched Places via eLoc as markers top of MapmyIndia Maps. 

The plugin can be used in combination with our Interactive Map JS libraries.

The SDK offers the following basic functionalities: 
1. Ability to render places directly using eLoc on MapmyIndia Maps SDK.
2. A MapmyIndia.elocMarker() method to initiate rendering of Places on the map specified with eLoc(s) on the map.
3. Ability to add listeners on marker events, remove markers, customize icons and get fitbounds of the markers. 
4. Ability to make markers draggable and add annotations (info popups + customizable popups).


## Live Demo

Visit the following link for visiting the live demo: 

[LIVE DEMO](https://www.mapmyindia.com/api/advanced-maps/doc/sample/mapmyindia_elocMarkerPlugin)

The above implementation uses MapmyIndia Interactive Map JS library as map rendering framework showcasing integration of marker plugin.

## Implementation

### Adding the MapmyIndia Marker plugin script

#### Script URL

```js
<script src="https://apis.mapmyindia.com/advancedmaps/api/{token-OR-JWT-key}/map_sdk_plugins"></script>
```

### 1. Initializing the Marker plugin

#### Method

`MapmyIndia.elocMarker()`

```js
/*marker plugin initialization*/
var markerOptions={
	map:map,
	eloc:[‘mmi000’,’123zrr’],
	popupHtml:[“<h1>MMI</h1>”,”<h1>Agra</h1>”],
	html:[“1”,”2”],
	icon:{url:’2.png’,width:30,height:45}
}

var obj=MapmyIndia.elocMarker(markerOptions);
```

OR

```js
var obj=MapmyIndia.elocMarker({map:map,eloc:'mmi000',popupHtml="<h1>MMI</h1>"});
```

#### Mandatory Parameters
1. `map`: object > vector map or raster map object from respective MapmyIndia Map SDKs.
2. `eLoc(s)`: array of strings containing the eLoc(s) which need to be showcased on the map. <br> e.g. 
    ```html
    [‘mmi000’,’123zrrr’]
    ```

#### Optional Parameters
1. `html`: (string or html) Text which needs to be written over the marker or if there is a need for further customization, then this param can also take in HTML div. <br>
e.g. 
    ```html
    'MapmyIndia'
    ```
    OR 
    ```
    [“<b>MMI</b>”,”<b>AGRA</b>”]
    ```
2. `popupHtml`: (string or HTML) What needs to be displayed when marker is clicked. <br>e.g. 
    ```
    [“<h1>MapmyIndia</h1>”,”<p>Agra</p>”]
    ```
3. `popupOptions`: (object) if the popup/annotation needs to be customized further. 
The following are the sub-params for the object: 
    - `className`: the class name of the annotation object.
    - `offset`: the offset positioning from the marker.
    - `openPopup`: (boolean) indicating if the pop needs to be open on addition of marker or not as default.
    <br> e.g. 
    ```js
    {
        className:’myClass’,
        offset:{},
        openPopup:true //open popup as default with add marker
     }
    ```
4. `icon`: (object) the customized marker icon options. The following are the sub-params for the object: 
    - `url`: the URL specifying the marker image.
    - `width`: width of the marker icon.
    - `height`: height of the marker icon.
    - `offset`: offset positioning of the marker's anchor.
    - `popupAnchor`: positioning of the marker popup's anchor.
    <br>
    
    e.g. 
    ```js
    {
        url:'https://apis.mapmyindia.com/map_v3/2.png',
        width:30,
        height:40,
        offset:[20,40],
        popupAnchor:[-5,-40]
    }
    ```
5. `draggable`: (boolean) to set the marker(s) as draggable or not.    

<br>

### 2. Method for getting all markers to fit in a viewbound
#### Method
`fitbounds()`

```js
obj.fitbounds(options); //options are optional e.g. {padding:100}
```

- `padding`: option can be used to setup a padding around the viewbound to fit the markers in.

### 3. Method for removing markers
#### Method
`remove()`

```js
obj.remove();
```

### 4. Method for adding event listeners on the marker
#### Method
`addListener()`

```js
obj.addListener(event,callback);
```

Example: 
```js
obj.addListener(‘click’,function(data){console.log(data);});
```

### 5. Method for removing event listeners on the marker
#### Method
`removeListener()`

```js
obj.removeListener(event);
```

Example: 
```js
obj.removeListener(‘click’);
```

### 6. Method for setting icons for markers
#### Method
`setIcon()`

```js
obj.setIcon(‘url.png’); //replaces all marker's icon.
```

OR

```js
obj.setIcon(‘url.png’,’mmi000’); //replaces single marker's icon for the provided eLoc.

```

### 7. Method for setting pophtml for markers
#### Method
`setPopup()`

```js
obj.setPopup({content:"<h1>MapmyIndia</h1>"}); //replaces all marker's pop up values.
```

OR

```js
obj.setPopup({content:"<h1>MapmyIndia</h1>",eloc:'123zrr'}); //replaces single marker's popup value for the provided eLoc.
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
