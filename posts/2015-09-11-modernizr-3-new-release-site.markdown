---
layout: post
title:  "Modernizr 3: A new release and website"
author: Modernizr
---

After what appears an eternity to us and the wider development community we are ecstatic to announce the release of Modernizr 3.0! This is a massive release and from our last release almost 2.5 years have passed - an unacceptable timeline. We plan to fix this and have faster releases where it makes sense.

### What's new and exciting?

A lot! We restructured how we write our detects. we no longer have the concept of core tests, and we redesigned and built the site from the ground up to give the website a refresh as well as make the builder a whole lot more powerful for beginners and advanced users. From just creating a simple build to grabbing a config, to implementing in your build process, through to a really cool solution of dynamically creating a custom package that can be installed via bower.

Along with this internal restructure, we’ve added over 100 new detects by the community!

### Modernizr changes:

The internal structure of Modernizr has been completely revamped, making it easier to contribute to and easier to customize/extend
Modernizr’s licensing has changed: we’ve moved from a BSD license to MIT. ([#679](https://github.com/Modernizr/Modernizr/issues/679))

#### Detects

* 99 new detects and counting (see [#1230](https://github.com/Modernizr/Modernizr/issues/1230) for the full list)
* No detect names are hyphenated anymore; e.g. `battery-api` → `batteryapi`, `flexbox-legacy` → `flexboxlegacy`, etc ([#719](https://github.com/Modernizr/Modernizr/issues/719), [#782](https://github.com/Modernizr/Modernizr/issues/782))
* `Modernizr.contentsecuritypolicy` has been removed, as the JS API it was testing is deprecated ([#1461](https://github.com/Modernizr/Modernizr/issues/1461))
* `Modernizr.touch` has been removed in favor of `touchevents` and `pointerevents` ([#548](https://github.com/Modernizr/Modernizr/issues/548))
* `Modernizr.pointerevents` now detects DOM PointerEvent support, rather than CSS pointer-events ([#800](https://github.com/Modernizr/Modernizr/issues/800))
* Detect for CSS pointer-events is now called `csspointerevents` ([#800](https://github.com/Modernizr/Modernizr/issues/800))
* Fixed false-positives in `fontface` detect ([#1147](https://github.com/Modernizr/Modernizr/issues/1147))
* Our tests for Flexbox have been revised to better match developers’ expectations:
  * `Modernizr.flexbox` returns true if flex-basis is supported – which represents a “reasonable” modern spec implementation (Chrome, FF, Safari and IE11 all pass this)
  * `Modernizr.flexwrap` has been added to detect features missing from Firefox’s implementation
  * `Modernizr.flexboxtweener` has been added to detect the implementation used by IE10
  * `Modernizr.flexboxlegacy` remains unchanged
* WebGL detect is now more reliable, using [HTMLCanvasElement.supportsContext()](http://www.w3.org/TR/2013/WD-html51-20130528/embedded-content-0.html#dom-canvas-supportscontext) where available ([#689](https://github.com/Modernizr/Modernizr/issues/689))
* WebGL extension enumerations are now attached to `Modernizr.webglextensions` rather than `Modernizr.webgl`
* The `datauri` detect now has a `over32kb` subproperty which will be true if the browser supports data URIs longer than 32 kB ([#321](https://github.com/Modernizr/Modernizr/issues/321))
* `audio` detect now also checks support for the Ogg Opus codec, exposed as `Modernizr.audio.opus` ([#699](https://github.com/Modernizr/Modernizr/issues/699))
* `audiodata` detect has been removed, because the implementation was very poor; this spec has been deprecated in favor of the Web Audio API ([#1019](https://github.com/Modernizr/Modernizr/issues/1019))
* `video` detect now has an `hls` subproperty representing support for the HLS video format ([#1317](https://github.com/Modernizr/Modernizr/issues/1317))
* `todataurljpeg`, `todataurlpng` and `todataurlwebp` are no longer asynchronous ([#802](https://github.com/Modernizr/Modernizr/issues/802))
* `fullscreen` detect has been updated to use `document.exitFullScreen` rather than the prefixed versions of `document.cancelFullScreen` as per [the latest spec](https://fullscreen.spec.whatwg.org/) ([#739](https://github.com/Modernizr/Modernizr/issues/739))
* `indexeddb` detect now has a `deletedatabase` subproperty, representing support for the `indexedDB.deleteDatabase()` method which isn’t implemented in some browsers ([#1238](https://github.com/Modernizr/Modernizr/issues/1238))
* `webp` detect now has `lossy`, `lossless` and `alpha` subproperties, representing support for various variants of the WebP format; the root `webp` property still represents basic lossy support ([#1229](https://github.com/Modernizr/Modernizr/issues/1229))
* Fixed a bug in `cssvwunit`, `cssvminunit` and `cssvmaxunit` which could give incorrect results when scrollbars are present ([#1045](https://github.com/Modernizr/Modernizr/issues/1045))
* Fixed a bug in `emoji` detect where the test could stop working once minified ([#899](https://github.com/Modernizr/Modernizr/issues/899))
* Fixed a bug in `regions` detect where wrong result could be given when page is zoomed ([#940](https://github.com/Modernizr/Modernizr/issues/940))
* Fixed a bug in `csstransforms3d` detect where wrong result could be given when page is zoomed ([#760](https://github.com/Modernizr/Modernizr/issues/760))
* Fixed a false-positive for the `cssscrollbar` detect in IE9 ([#698](https://github.com/Modernizr/Modernizr/issues/698))
* Fixed a bug where `indexeddb` would throw an error if indexedDB was disabled via a browser flag ([#798](https://github.com/Modernizr/Modernizr/issues/798))
* Fixed various false-positives in `fileinput` detect ([#772](https://github.com/Modernizr/Modernizr/issues/772))
* Fixed various incorrect results in `history` detect ([#733](https://github.com/Modernizr/Modernizr/issues/733), [#1471](https://github.com/Modernizr/Modernizr/issues/1471))
* Fixed a false-positive for `cookies` detect in IE9 ([#666](https://github.com/Modernizr/Modernizr/issues/666))
* Fixed a false-negative for `csstransforms3d` in WebKit browsers when certain styles are present on the page ([#740](https://github.com/Modernizr/Modernizr/issues/740))
* Fixed a bug where a page reload could crash Safari 5.1 ([#524](https://github.com/Modernizr/Modernizr/issues/524))
* Fixed `cssmask` detect (a typo meant it was ineffective) ([#671](https://github.com/Modernizr/Modernizr/issues/671))
* Fixed `userselect` detect (a typo meant it was ineffective) ([#671](https://github.com/Modernizr/Modernizr/issues/671))
* Fixed a bug in `displaytable` detect when page is in RTL ([#716](https://github.com/Modernizr/Modernizr/issues/716))
* Improved accuracy of `xhr2` detect in Firefox 3.6 ([#1178](https://github.com/Modernizr/Modernizr/issues/1178))
* Improved accuracy of `customprotocolhandler` detect in Android 2.x ([#992](https://github.com/Modernizr/Modernizr/issues/992))
* Blacklisted Android 1.x & 2.x from passing the `csstransforms` detect, because it’s excessively buggy ([#903](https://github.com/Modernizr/Modernizr/issues/903))
* Fixed `backgroundblendmode` detect ([#1420](https://github.com/Modernizr/Modernizr/issues/1420))

#### APIs

* Modernizr used to include a `Function.prototype.bind` polyfill (this was documented, but was somewhat hidden); this has been removed ([#1278](https://github.com/Modernizr/Modernizr/issues/1278))
* `testProp()`, `testAllProps()` and `prefixed()` now use [`CSS.supports()`](https://developer.mozilla.org/en-US/docs/Web/API/CSS.supports) under the hood for most CSS feature detects where available, improving performance and accuracy ([#818](https://github.com/Modernizr/Modernizr/issues/818))
* `Modernizr.load` has been deprecated in favor of using [yepnope.js](http://yepnopejs.com/) directly; from v3.0, yepnope.js must be included in the page in order for `Modernizr.load` to work: calling `.load()` will simply pass the arguments on to `yepnope()`; this will be removed fully in a future release ([#1241](https://github.com/Modernizr/Modernizr/issues/1241))
* New `Modernizr.on()` API, for handling asynchronous detects ([#622](https://github.com/Modernizr/Modernizr/issues/622))
* New `prefixedCSS()` API, which functions like `prefixed()` but returns the prefixed property name in kebab-case (hyphenated, as used in CSS) instead of camelCase ([#848](https://github.com/Modernizr/Modernizr/issues/848))
* `testProp()`, `testAllProps()`, `prefixed()` and `prefixedCSS()` now accept property names in either camelCase or kebab-case; for prefixed*() the format of the response depends on which function you call: `prefixed()` always returns camelCase, `prefixedCSS()` always returns kebab-case) ([#848](https://github.com/Modernizr/Modernizr/issues/848))
* New `noPrefixes` build option, which forces feature detects to only return true if the feature is supported without a vendor prefix ([#1082](https://github.com/Modernizr/Modernizr/issues/1082))
* New `enableJSClass` build option, which determines whether or not to add js/no-js classes to the `<html>` element when Modernizr runs; true by default ([#1385](https://github.com/Modernizr/Modernizr/issues/1385))
* `hasEvent()` previously used “appropriate” elements for certain tests: submit would be tested against a `<form>` element, error would be tested against an `<img>` element, etc; this is no longer the case – for consistency, all will be tested against a `<div>`, unless otherwise specified by the optional elem argument ([#636](https://github.com/Modernizr/Modernizr/issues/636))
* `hasEvent()`'s optional elem argument can now be an element or simply a tag name, e.g. `Modernizr.hasEvent('click', 'a')` ([#636](https://github.com/Modernizr/Modernizr/issues/636))
* If a classPrefix is specified as a build option, it will be applied to no-js/js classes as well (previously this only applied to feature classes) ([#1031](https://github.com/Modernizr/Modernizr/issues/1031))
* Fixed a bug where classPrefix wasn’t applied to the class set for the first-executed feature detect ([#1053](https://github.com/Modernizr/Modernizr/issues/1053))
* `testProp()` and `testAllProps()` now accept up to 3 arguments: `testProp(prop, [value, [skipValueTest]])`; if a value is provided, Modernizr will ensure that value is supported for the named CSS property, delegating to CSS.supports() where available; if skipValueTest is true (default is false), the value test won’t be conducted when CSS.supports() isn’t available
* `addTest()` will now set subproperties if given a property name containing a period (.), which can be used for defining custom structured detects, or for extending existing detects (e.g. adding custom codec detects to `Modernizr.audio`) ([#1089](https://github.com/Modernizr/Modernizr/issues/1089)) ***(buggy: [#1355](https://github.com/Modernizr/Modernizr/issues/1355))***
* Fixed a bug where calling `Modernizr.prefixed()` with an obj argument which doesn’t support binding would throw an exception ([#1014](https://github.com/Modernizr/Modernizr/issues/1014))
* Fixed a bug where calling `Modernizr.mq()` inside a hidden iframe would throw an error in Firefox ([#886](https://github.com/Modernizr/Modernizr/issues/886))

### The website

We started out revamping the builder to make it easier to find the detects you needed and evolved into a complete revamp of the website.

### Some things to point out:

* The website uses service workers so after you’ve created your build in theory you can do the same offline
* You can search for a detect in real time on the download page.
* Each detect now has a special comment that we parse and display on the download page, with handy information about the detect including polyfills and links.
* Best of all it’s open source so if you find issues please report or fix them!

### Thanks

Of course we can't thank the community enough for their massive contributions to Modernizr 3.0 all 86 of them!

[AlbertoElias](https://github.com/AlbertoElias), [BYK](https://github.com/BYK), [DannyJoris](https://github.com/DannyJoris), [MoOx](https://github.com/MoOx), [NikV](https://github.com/NikV), [RReverser](https://github.com/RReverser), [Rowno](https://github.com/Rowno), [SimenB](https://github.com/SimenB), [SlexAxton](https://github.com/SlexAxton), [TalAter](https://github.com/TalAter), [Wilto](https://github.com/Wilto), [Yomguithereal](https://github.com/Yomguithereal), [alrra](https://github.com/alrra), [anenviousguest](https://github.com/anenviousguest), [aroben](https://github.com/aroben), [atdt](https://github.com/atdt), [ausi](https://github.com/ausi), [bportnoy](https://github.com/bportnoy), [brendankenny](https://github.com/brendankenny), [burnersk](https://github.com/burnersk), [cagerton](https://github.com/cagerton), [calweb](https://github.com/calweb), [candrews](https://github.com/candrews), [chrisjlee](https://github.com/chrisjlee), [danbeam](https://github.com/danbeam), [darcyclarke](https://github.com/darcyclarke), [dbow](https://github.com/dbow), [ddprrt](https://github.com/ddprrt), [devongovett](https://github.com/devongovett), [devote](https://github.com/devote), [dmethvin](https://github.com/dmethvin), [doctyper](https://github.com/doctyper), [drublic](https://github.com/drublic), [edmellum](https://github.com/edmellum), [emilchristensen](https://github.com/emilchristensen), [fgnass](https://github.com/fgnass), [filaraujo](https://github.com/filaraujo), [frederfred](https://github.com/frederfred), [frob](https://github.com/frob), [gaearon](https://github.com/gaearon), [garrypolley](https://github.com/garrypolley), [genintho](https://github.com/genintho), [grayghostvisuals](https://github.com/grayghostvisuals), [hzoo](https://github.com/hzoo), [jacobrossi](https://github.com/jacobrossi), [janroures](https://github.com/janroures), [javiercejudo](https://github.com/javiercejudo), [jmartin84](https://github.com/jmartin84), [jokeyrhyme](https://github.com/jokeyrhyme), [jon301](https://github.com/jon301), [jonathanong](https://github.com/jonathanong), [jongrover](https://github.com/jongrover), [jtangelder](https://github.com/jtangelder), [kkirsche](https://github.com/kkirsche), [komachi](https://github.com/komachi), [kristerkari](https://github.com/kristerkari), [lbesson](https://github.com/lbesson), [mathiasbynens](https://github.com/mathiasbynens), [mikach](https://github.com/mikach), [mrkiffie](https://github.com/mrkiffie), [nok](https://github.com/nok), [patrickkettner](https://github.com/patrickkettner), [paulirish](https://github.com/paulirish), [robocoder](https://github.com/robocoder), [robwierzbowski](https://github.com/robwierzbowski), [rose](https://github.com/rose), [rrrene](https://github.com/rrrene), [rxaviers](https://github.com/rxaviers), [ryanseddon](https://github.com/ryanseddon), [silverwind](https://github.com/silverwind), [slavanga](https://github.com/slavanga), [ssidorchick](https://github.com/ssidorchick), [steveyken](https://github.com/steveyken), [stucox](https://github.com/stucox), [svinkle](https://github.com/svinkle), [swaydeng](https://github.com/swaydeng), [teebot](https://github.com/teebot), [thanpolas](https://github.com/thanpolas), [tnajdek](https://github.com/tnajdek), [tomgco](https://github.com/tomgco), [triblondon](https://github.com/triblondon), [vlajos](https://github.com/vlajos), [wilddeer](https://github.com/wilddeer), [zachleat](https://github.com/zachleat), [zeno](https://github.com/zeno), [zhorvath](https://github.com/zhorvath)

A few worthy call outs, Patrick Kettner who came in and contributed an enormous amount of effort and work to get 3.0 to the state it is, without him we wouldn't of got to this release. Stu Cox who also came onto the scene and contributed a huge amount of work and Joe Critchley who took on updating the look and feel of the our new shiny website.
