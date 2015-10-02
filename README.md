# VMAP Javascript Library

[![Build Status](https://travis-ci.org/dailymotion/vmap-js.png)](https://travis-ci.org/dailymotion/vmap-js)

Complies with [VMAP 1.0.1 spec](http://www.iab.net/media/file/VMAP.pdf).

## Usage

``` javascript
// Fetch VMAP as XML using XMLHTTPRequest
xml = myVMAPFetcher();

// Parse VMAP
var vmap = new VMAP(xml);
```

## API

### VMAP

#### Properties

* `version`: The VMAP version (should be 1.0).
* `adBreaks`: An array of `VMAPAdBreak` objects.
* `extensions`: An array of XML nodes for each extension left as-is if any.

### VMAPAdBreak

Provides information about an ad break.

#### Properties

* `timeOffset`: Represents the timing of the ad break.
* `breakType`: Identifies whether the ad break allows "linear", "nonlinear" or "display" ads.
* `breakId`: An optional string identifier for the ad break.
* `repeatAfter`: An option used to distribute ad breaks equally spaced apart from one another along a linear timeline.
* `adSource`: A `VMAPAdSource` object.
* `trackingEvents`: An array of `Object` with tracking URLs
    * `event`: The name of the event to track for the element. Can be one of breakStart, breakEnd or error.
    * `uri`: The URI of the tracker.
* `extensions`: An array of XML nodes for each extension left as-is if any.

### VMAPAdSource

Provides the player with either an inline ad response or a reference to an ad response.

#### Properties

* `id`: Ad identifier for the ad source.
* `allowMultipleAds`: Indicates whether a VAST ad pod or multple buffet of ads can be served into an ad break.
* `followRedirects`: Indicates whether the video player should honor the redirects within an ad response.
* `vastAdData`: Contains an embedded VAST response.
* `adTagURI`: Contains a URI to the VAST.
* `customData`: Contains custom ad data.
