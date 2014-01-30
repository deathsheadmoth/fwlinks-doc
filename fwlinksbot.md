## fwlinksbot

fwlinksbot is special. He tells you about stuff that goes on as it happens (first, actually). You should _want_ him in your channel. If you do, [contact me](http://www.icj.me/contact)!

More about this:

When any event happens in terms of the fwlinks updaters (i.e. firmware, iTunes, redsn0w, PwnageTool, iFaith, sn0wbreeze, etc release or SHSH signing changes), **fwlinksbot** actually posts by default to the IRC channels that he's in, in a format similar to this:

`[10:55] <+fwlinksbot> [Update] Something awesome has happened!` (but kinda more detailed :P)

And yes, he's a "he".

So, onto the commands.

## Commands

Commands are as follows:

* `!fw`, `!firmware` - for firmware releases
  following the format: `!fw <identifier> (buildid/version) (request)`
* `!it`, `!itunes` - for iTunes releases
  following the format: `!it <Operating System> (version) (request)`
* `!rs`, `!redsn0w` - for redsn0w releases
  following the format: `!rs <Operating System> (version) (request)`
* `!pt`, `!pwnagetool` - for pwnagetool releases (got the idea yet? :P)
  following the format: `!pt (version) (request)`
* `!tss` - for TSS (SHSH signing!) requests - powered by [Neal](http://twitter.com/iNeal)'s API.
  following the format: `!tss <identifier/version/buildid>`
* `!shsh` - for finding out SHSH blobs found on Cydia's SHSH cache server.
  following the format: `!shsh <ecid>`

Where `<item>` indicates a required field. If the items in brackets are not found, they will default to the following:

* `(version)` to `latest`
* `(request)` to `url`

## Requests:

Where:

* `<identifier>` is the *identifier* of the device you want, or the *boardconfig*. e.g. _iPhone4,1_ **or** _n94ap_
* `<buildid>` is the BuildIdentifier of the firmware file, found in the BuildManifest.plist or Restore.plist of the IPSW file. Also the filename of the IPSW (see diagram below)
* `<version>` is the version of the IPSW/tool (see diagram below)
* `<request>` is the data you wish to request - see the [Firmware Links API documentation](http://api.ios.icj.me/docs/Firmware#requests) for all possibilities.

<pre class="code" style="width: auto; min-width: auto;">
e.g. iPhone3,1_4.1_8B117_Restore.ipsw
     |_______| |_| |___|
         |      |    |
         |      |    \----- BuildID: 8B117
         |      \---------- Version: 4.1
         \----------------- Identifier/device: iPhone3,1
</pre>


## Some Examples

* `!fw iPhone4,1`
* `!it Windows`
* `!rs Windows 0.9.15b3 url`
* `!fw iPhone2,1 latest version`
* `!fw n81ap latest datefound`
* `!iTunes Windows 11.0.5 url`
* `!tss iPhone3,1`
* `!tss 4.2.1`

This documentation and the fwlinksbot will most likely receive updates in the near future.
