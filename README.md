LiveReload.js
=============

UNFINISHED WORK IN PROGRESS.

This repository contains the JavaScript file served to the browsers by various LiveReload servers:

* [LiveReload 2.x GUI for Mac](http://livereload.com/)
* [guard-livereload](https://github.com/guard/guard-livereload)


What is LiveReload?
-------------------

LiveReload is a tool for web developers and designers. See [livereload.com](http://livereload.com/) for more info.

LiveReload.js connects to a LiveReload server via web sockets and listens for incoming change notifications. When CSS or image file is modified, it is live-refreshed without reloading the page. When any other file is modified, the page is reloaded.


Reimplementation
----------------

Previously, the described logic has been part of LiveReload browser extensions. This repository contains an effort to reimplement the logic so that it:

* is standalone, [following the new approach to browser extensions](http://help.livereload.com/discussions/suggestions/12),
* is covered with tests,
* is modular and maintainable,
* implements a [new future-proof protocol](http://help.livereload.com/kb/ecosystem/livereload-protocol).

Currently, the code is missing the 'live refreshing' part — it reloads the whole page on any change. Aside from that, it is fully working.

Both old and new protocols are supported, so this file can readily work with existing LiveReload servers.


CommonJS modules
----------------

New code is split into CommonJS-style modules, stitched together using a simple Rakefile.

I've tried to use Stitch.js, but it did not want to autorun startup code from startup.coffee module. The custom-made regexp-ridden approach works so much better (and produces much clearer code).
