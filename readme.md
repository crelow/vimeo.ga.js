# Google Analytics Vimeo Video Tracking
A Google Analytics plugin for measuring Vimeo Player Events. The plugin supports Universal Analytics, Classic Google Analytics, and Google Tag Manager.

## Usage
Include the scripts in the body section of the HTML document, just before the `</body>` tag. You’ll need to be running on a web server instead of opening the file directly in your browser. Flash and JS security restrictions will prevent the API from working when run locally.

### Basic
```html
<iframe src="//player.vimeo.com/video/22439234?api=1" id="vimeo-player" width="640" height="390" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
<script src='https://ajax.googleapis.com/ajax/libs/jquery/1.4.3/jquery.min.js'></script>
<script src="path/to/vimeo.ga.min.js"></script>
```
### With some options
```html
<iframe src="//player.vimeo.com/video/22439234?api=1" id="vimeo-player" width="640" height="390" frameborder="0" data-progress="true" data-seek="true" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
<script src='https://ajax.googleapis.com/ajax/libs/jquery/1.4.3/jquery.min.js'></script>
<script src="path/to/vimeo.ga.min.js"></script>
```
The **data-progress** and **data-seek** attributes enable tracking of progress and skip events.

The iframe embeds a Vimeo video player and allows Vimeo to serve an HTML5 player rather than a Flash player for mobile devices that do not support Flash.

## Event Tracking
All player events are only tracked once. Restarting the video will not reset the event trackers.

### Basic event trackers
* Category: Vimeo
* Action:
  * **Started video**: when the video starts playing.
  * **Paused video**: when the video is paused.
  * **Resumed video**: when the video starts playing when it was paused.
  * **Completed video**: when the video reaches 100% completion.
  * **Skipped video**: when the video is skipped forward or backward.
* Label: URL of embedded video on Vimeo.

##### Example Classic Analytics
```js
_gaq.push(['_trackEvent', 'Vimeo', 'Started video', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Paused video', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Resumed video', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Completed video', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Skipped video forward or backward', 'http://player.vimeo.com/video/22439234', undefined, true]);
```

##### Example Universal Analytics
```js
ga('send', 'event', 'Vimeo', 'Started video', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Paused video', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Resumed video', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Completed video', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Skipped video forward or backward', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
```

##### Example Google Tag Manager
```js
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Started video', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Paused video', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Resumed video', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Completed video', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Skipped video forward or backward', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
```

### Progress event trackers

* Category: Vimeo
* Action:
  * **25% Progress**: when the video reaches 25% of the total video time.
  * **50% Progress**: when the video reaches 50% of the total video time.
  * **75% Progress**: when the video reaches 75% of the total video time.
* Label: URL of embedded video on Vimeo.

##### Example Classic Analytics
```js
_gaq.push(['_trackEvent', 'Vimeo', 'Played video: 25%', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Played video: 50%', 'http://player.vimeo.com/video/22439234', undefined, true]);
_gaq.push(['_trackEvent', 'Vimeo', 'Played video: 75%', 'http://player.vimeo.com/video/22439234', undefined, true]);
```

##### Example Universal Analytics
```js
ga('send', 'event', 'Vimeo', 'Played video: 25%', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Played video: 50%', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
ga('send', 'event', 'Vimeo', 'Played video: 75%', 'http://player.vimeo.com/video/22439234', undefined, {'nonInteraction': 1});
```

##### Example Google Tag Manager
```js
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Played video: 25%', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Played video: 50%', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
dataLayer.push({'event': 'Vimeo', 'eventCategory': 'Vimeo', 'eventAction': 'Played video: 75%', 'eventLabel': 'http://player.vimeo.com/video/22439234', 'eventValue': undefined, 'eventNonInteraction': true});
```

### Bounce rate
The event trackers do not impact bounce rate of the page which embeds the video. The value of the opt_noninteraction parameter is set to `true` or `1`.

## Google Tag Manager
If you'd like to integrate with Google Tag Manager, the dataLayer variable names are below.

| Macro Name            | Data Layer Variable       | 
| --------------------- | ------------------------- |
| Event Category        | `{{eventCategory}}`       |
| Event Action          | `{{eventAction}}`         |
| Event Label           | `{{eventLabel}}`          |
| Event Value           | `{{eventValue}}`          |
| Event Non-Interaction | `{{eventNonInteraction}}` |

Use the GTM event `Vimeo` to fire the Universal or Classic Google Analytics event tag.

The GTM container tag could also be used to include the plugin inside a page containing the video. Create a custom HTML tag and trigger this tag so that this script fires on gtm.dom (`{{event}}` equals `gtm.dom`), meaning it will fire once the DOM is ready.

## Browser Support
Tested in the latest versions of Chrome, Firefox, Safari, and IE. Also tested on iOS.

## Requirements
* jQuery 1.4.3 or higher
* Classic Google Analytics Tracking Code (asynchronous), Universal Analytics Tracking Code or Google Tag Manager container code
* The end user must be using a browser that supports the HTML5 postMessage feature. Most modern browsers support postMessage, though Internet Explorer 7 does not support it.

## Issues
Have a bug? Please create an [issue](https://github.com/sanderheilbron/vimeo.ga.js/issues) here on GitHub!

## Contributing
Want to contribute? Great! Just fork the project, make your changes and open a [pull request](https://github.com/sanderheilbron/vimeo.ga.js/pulls).

## Changelog
### 0.4 (June 22, 2014)
* Support for Universal Analytics and Google Tag Manager.
* 'Resumed video' added as basic event tracker.
* Code cleanup.
* Updated documentation.

### 0.3 (May 15, 2014):
* Checks if Vimeo iframe is present to prevent JS error on pages without iframe.
* Fixed a bug when the page contains other iframes.
* Support for new Vimeo iframe usage guidelines, the script supports HTTP and HTTPS protocol.

### 0.2 (February 3, 2013):
 * Code cleanup.
 * Fixed a bug in pause event tracking.
 * Updated documentation.

### 0.1 (October 12, 2012):
 * Initial release.

## License
Licensed under the MIT license.

Copyright (c) 2014 [Sander Heilbron](http://www.sanderheilbron.nl)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
