## fwlinksbot

fwlinksbot is special. He tells you about stuff that goes on as it happens (first, actually). You should _want_ him in your channel. If you do, [contact me](http://www.icj.me/contact)!

So, onto the commands.

## Commands

There are three distinct commands.

* `!fw` - for firmware, iTunes, redsn0w and PwnageTool requests.
* `!tss` - for TSS (SHSH signing!) requests - powered by [Neal](http://twitter.com/iNeal)'s API.
* `!shsh` - for finding out SHSH blogs found on Cydia's SHSH cache server.

## The syntax

### !fw requests

_**The following is for firmwares only!**_

The syntax is as follows:

* `!fw [device] [version] [request]` - see explanations below for the meanings of each of these.
* `!fw [device] [buildid] [request]` - noting that versions are easier for users to remember (_i.e._ the first command is probably more suited to usage in IRC)


#### Requests:

* `[device]` - the *identifier* of the device you want, or the *boardconfig*. e.g. _iPhone4,1_ **or** _n94ap_
* `[buildid]` - the BuildIdentifier of the firmware file, found in the BuildManifest.plist or Restore.plist of the IPSW file. Also the filename of the IPSW (see diagram below)
* `[version]` - the version of the IPSW (see diagram below)
* `[request]` - the data you wish to request - see the [Firmware Links API documentation](http://api.ios.icj.me/docs/Firmware#requests) for all possibilities.

You will then be returned the data you wish in this form:

`[request]: [data]` where `[data]` is what you wanted :)

_**For all other types**_

_i.e._ iTunes, redsn0w, PwnageTool

The request follows this syntax:

`!fw [product] ([version])` - **N.B.** `[version]` is not required, and in some cases not yet supported (work in progress). The default is to return the _latest_ version.Which is probably of the most use to you anyway.

### !tss requests

The `!tss` requests operate on a per-device basis, and are for finding out firmwares *currently being signed* by Apple. The request format is as follows:

`!tss [request]` - where `[request]` is one of the following:

* `[device]` - the *identifier* of the device you want e.g. `iPhone4,1`
* `[boardconfig]` - the *boardconfig* that you want e.g. `n81ap`
* `[version]` - the version of the firmware e.g. `4.2.1`
* `[buildid]` - the buildid of the firmware e.g. `8B117`

### !shsh requests

The `!shsh` command operates on a per-device basis, and is useful for finding out which SHSH blobs saurik has on his server. The request format is as follows:

`!shsh [ecid]` - where `[ecid]` is the ECID of the device, in either decimal or hexadecimal form.

## Some Examples

* `!fw iPhone2,1 latest url`
* `!fw n81ap latest datefound`
* `!fw iTunes` - latest version
* `!fw redsn0w` - latest version
* `!fw iTunes 11.0.5`
* `!tss iPhone3,1` - TSS request
* `!fw PwnageTool` - latest version

This documentation and the fwlinksbot will most likely receive updates in the near future.