# kindle-weather-dashboard

This fork of https://github.com/matopeto/kindle-weather-dashboard lets you show
a 4-day weather forecast instead of the next 12 hours.

# NOTICE

_This fork depends on the Open Weather One Call API 3.0, which allows for 
1000 calls/day for free. But you must give them a credit card and subscribe._

The subscription page lets you restrict your calls/day to 1000 so you 
should never be charged. Also this script only updates every 2 hours.

* [One Call API 3.0 | https://openweathermap.org/api/one-call-3]
* [One Call Subscription Details | https://openweathermap.org/full-price]

We only support Lat/Lon (ex: `lat=50&lon=14`) because 
that's the API 3.0 supports. We do use the reverse geolocation API to 
get the city, so it's certainly possible to fix the url query code to
use the forward geolocation API to lookup city. But I'm already out of
my depth with this hack. :-}

## Features

* **current weather and temperature**
* **forecast for the next 4 days**, in landscape mode for **5 days**
* **sunrise and sunset**
* **Moon phase**

## Options

* **portrait and landscape mode**
* **landscape mode on Paperwhite!!** see configuration
* configurable place, units, language
* automatic night mode
* tested on **Kindle 3/4/5, Paperwhite 3, iPad Air**, *it may also work on other Kindles and devices*,

Weather and forecast source: https://openweathermap.org/

Icons source: https://github.com/erikflowers/weather-icons

<img src="real_devices.jpg" width="300" alt="Dashboard on real devices" />

# How to run directly on the Kindle (tested on Kindle PW 3)
1. clone or download repository
2. generate your free API key (AppId) at http://openweathermap.org/appid
3. rename `config.js.sample` to `config.js` and set the parameters you need (all parameters are optional and can be set in the HTML webpage `config.html`, but I recommend setting at least the `api_appId`)
4. copy the folder with all files to the root of Kindle storage
5. disable the screensaver on your Kindle:
  * press the search button (or keyboard button on Kindle 4) on homescreen and type: `;debugOn` and press enter on the keyboard
  * press the search button (or keyboard button on Kindle 4) again and type: `~disableScreensaver` and press enter on the keyboard. (On Kindle Paperwhite, type: `~ds` - with new firmware this may not be possible, but see these [instructions](https://github.com/matopeto/kindle-weather-dashboard/issues/16) for a solution)
6. launch the browser on your Kindle and go to: `file:///mnt/us/kindle-weather-dashboard/index.html` (where `kindle-weather-dashboard` is the folder in the root of your Kindle storage from step 4)

## Configuration
### with config.js
create a config.js file from config.js.sample and set variables:

* `api_locParams` - query parameters to set location (e.g. `lat=50&lon=14`, or `q=Paris`)
* `api_appId` - set your `API KEY (appId)` from http://openweathermap.org/appid
* `api_lang` - output language (e.g. `en`)
* `api_units` - units (e.g. `metric`, `imperial`)
* or you can set all parameters with the `api_params` variable (e.g. `q=Prague&appid=YOUR_API_KEY&lang=sk&units=metric`)
* `rotation` - set rotation (on Kindle Paperwhite) `ll` for left landscape, `lr` for right landscape, and `up` for upside down
* `night_mode` - `auto` - based on sunrise and sunset, `on` - always on, `HH-HH` (`22-06`) interval for on/off, `off` or `null` to disable
* `refreshTime` - refresh rate in milliseconds (default is 30 minutes)
* `utcOffset` - if not set, it is determined by location, `local` - local machine UTC offset, or custom UTC offset. (Because Kindle doesn't report the correct local time. You may need to change the value after the winter/summer time change)
* `tempType` - use `feelsLike` to show feels-like temperatures

See more: http://openweathermap.org/current and http://openweathermap.org/forecast5

### with url query parameters

* `appId` sets the appId
* `city` sets the city (e.g. `city=Paris`) ** UNSUPPORTED **
* `lat`, `lon` set location (e.g. `lat=50&lon=14`)
* `lang` and `units` for language and units :)
* `rotation` sets the rotation :)
* `utcOffset` sets UTC offset
* `tempType` sets temperature type (actual or feels like)

Examples:
* Dashboard for Prague, metric units, Slovak language: `http://YOUR_URL/?city=Prague&lang=sk&units=metric&appId=YOUR_API_KEY`
* Dashboard for a given GPS location, metric units, default language: `https://YOUR_URL/?lat=50&lon=14&units=metric&appId=YOUR_API_KEY`

## Screenshots

### Kindle 4
<img src="screenshot_kindle4.gif" width="300" alt="Kindle 4 screenshot" />

### Kindle Paperwhite 3
<img src="screenshot_paperwhite3.png" width="300" alt="Kindle Paperwhite 3 screenshot" />

### Real devices
<img src="real_devices.jpg" width="300" alt="Dashboard on real devices" />

