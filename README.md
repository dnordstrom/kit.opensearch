## Introduction

A search provider installer for [OpenSearch](http://www.opensearch.org) capable browsers---including provider XML for [Startpage](https://www.startpage.com/), [DuckDuckGo](https://www.duckduckgo.com/), [DeviantArt](https://www.deviantart.com/) People Search, etc. This initial version is just a simple installer script, to be loaded by a bookmarklet.

**Compatibility:** OpenSearch is implemented in Firefox (2+), Chrome, and IE (7+). Opera does not support OpenSearch&mdash;however, Opera 17+ Developer Previews feature a shiny new search engine manager. An Opera 18 preview is [available](http://my.opera.com/desktopteam/blog/) at the time of writing.

[Firefox Aurora](http://www.mozilla.org/firefox/aurora) is for the adventurous ones.

## To do

* Add simple bookmarklet to inject installer script on current page.
* Extend bookmarklet to show available providers, or create XML on-the-fly.
* Add guide for setting up provider for [Startpage](https://www.startpage.com/) with custom settings URL.

## Usage

### Install by inject &middot; &middot; &middot; bookmarklet

This is a simple method, but may be blocked if plugins such as NoScript for Firefox prevent [cross-site scripting (XSS)](https://en.wikipedia.org/wiki/Cross-site_scripting). This is a good thing, so please install [NoScript](http://noscript.net/) if you haven't already, along with [HTTPS Everywhere](https://www.eff.org/https-everywhere) to redirect to HTTPS whenever available.

*Due to [security concerns](https://trac.torproject.org/projects/tor/wiki/doc/ImportantGoogleChromeBugs), I cannot recommend Google Chrome.*

1. Drag <a href="javascript:(function(){var%20sUrl=prompt('Enter%20URL%20to%20JavaScript%20file');if(sUrl){var%20s=document.createElement('script');s.setAttribute('src',sUrl);document.getElementsByTagName('body')[0].appendChild(s);alert('Script%20injected!');}})();">this link</a> into your bookmarks&mdash;it's a bookmarklet that prompts for a URL to a Javascript file to inject, and appends a `script` tag to the document `body`.
2. Click it, then paste the URL to the installer (`install.js`), which should take care of the rest.

**Note:** At this time, the installer simply loads the DeviantArt People Search provider.

### Install by hand &middot; &middot; &middot; console

1. Load your browser's console. In Firefox, it's located at *Tools* -> *Web Developer* -> *Web Console*.
2. Call `window.external.AddSearchProvider(url)` with the URL to a provider XML file. For the DeviantArt People Search provider: `window.external.AddSearchProvider("https://gist.github.com/dnordstrom/6632592/raw/eb09e24d9624d1927f58e3516489834b44451027/deviantart_people_search_plugin-20130919.xml");`.
3. You will receive a confirmation dialog which completes the installation.

## License

<a href="http://www.wtfpl.net/"><img alt="WTFPL" src="http://www.wtfpl.net/wp-content/uploads/2012/12/logo-220x1601.png" height="96" width="132"></a>

Copyright © 2000 Daniel Nordstrom &lt;mrnordstrom@me.com&gt;<br>
This work is free. You can redistribute it and/or modify it under the
terms of the Do What The Fuck You Want To Public License, Version 2,
as published by Sam Hocevar. See the COPYING file for more details.