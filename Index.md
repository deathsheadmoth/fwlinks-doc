IPSW Downloads API Documentation
================================

_[previously "Firmware Links"](https://www.icj.me/blog/20140925/ipsw-downloads)_

A public API to request information from the [IPSW.me](http://ipsw.me) website.

This documentation is open source. If you find any issues, how about sending a [pull request](https://github.com/JustaPenguin/fwlinks-doc)?

You can now request from this API with SSL from the new domain `https://api.ipsw.me/` - and you totally should! Thanks to my friends at [CloudFlare](http://cloudflare.com). :-)

## Version 2

Available for the foreseeable future. Using API v2.1 is recommended.

* [Firmware](2/Firmware) - for requesting information about iOS firmwares.
* [iTunes](2/iTunes) - for requesting information about iTunes releases.
* [PwnageTool](2/PwnageTool) - for requesting information about PwnageTool.
* [redsn0w](2/redsn0w) - for requesting information about redsn0w.

## Version 2.1

The **changelog** for v2.1 can be found [here](2.1/Changelog). 

* [Firmware](2.1/Firmware) - for requesting information about iOS firmwares.
* [iTunes](2.1/iTunes) - for requesting information about iTunes releases.

Note that if you wish to request from the "PwnageTool" or "redsn0w" sections of the API, you must use v2. They were discontinued starting with v2.1.

## Misc

* [fwlinksbot](misc/fwlinksbot) - the IPSW.me IRC bot, which notifies channels of new releases, as well as providing access to parts of this API.

## Other Information

* Note that no parts of the API return beta firmware or OTA update information.
* Please **assign your application a user agent** when you request a link. This will make it easier to track the API usage.
* There is a PHP Class and example for using the API on my [GitHub](https://github.com/cj123/fwlinks-api).