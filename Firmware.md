## iOS Firmwares

The API v2 has been updated to be faster, prettier, and more epic than before. This does however mean some **significant changes** to the way the API is used. <strike>While v1 will remain running,</strike> It is recommended that you update your programs to use the new method of requesting information.

Before using the API please read all of this document.

## Contents

1. [Formatting the URLs/Syntax](#formatting)
2. [Requesting Data](#requests)
3. [Extras](#extras)
4. [Responses](#responses)
5. [Examples](#examples)
6. [Other Information](#other)

---

## 1. Formatting the URLs/Syntax<a id="formatting"></a>

In this section, the following key should be used:

* `[device]` - the *identifier* of the device you want, or the *boardconfig*. e.g. _iPhone4,1_ **or** _n94ap_
* `[buildid]` - the BuildIdentifier of the firmware file, found in the BuildManifest.plist or Restore.plist of the IPSW file. Also the filename of the IPSW (see diagram below)
* `[version]` - the version of the IPSW (see diagram below)
* `[request]` - the data you wish to request - see [Requesting Data](#requests) for all available requests.
* `[checksum]` - either the SHA1sum or MD5sum of the IPSW.

<pre class="code" style="width: auto; min-width: auto;">
e.g. iPhone3,1_4.1_8B117_Restore.ipsw
     |_______| |_| |___|
         |      |    |
         |      |    \----- BuildID: 8B117
         |      \---------- Version: 4.1
         \----------------- Identifier/device: iPhone3,1
</pre>

### 1.1. Using the device and BuildID

_This is the recommended method_

The request URL follows the syntax below:

`http://api.ios.icj.me/v2/[device]/[buildid]/[request](/dl)`

### 1.2. Using the device and version

The request URL follows the syntax below:

`http://api.ios.icj.me/v2/[device]/[version]/[requested data](/dl)`

**Warning** this request is not ideal, due to the fact that some versions have more than one firmware under that version. If this is the case, a `300 Multiple Choices` [status code](#responses) will be returned, with all the data in JSON format. _Just use the BuildID request method (1.1)_.

### 1.3. Using device and 'latest' OR 'earliest'

This allows you to select the latest/earliest data for a device.

The request URL follows the syntax below:

* `http://api.ios.icj.me/v2/[device]/latest/[requested data](/dl)` for latest
* `http://api.ios.icj.me/v2/[device]/earliest/[requested data](/dl)` for earliest

### 1.4. Using the MD5sum or SHA1sum of the IPSW file

The request URL follows the syntax below:

`http://api.ios.icj.me/v2/[checksum]/[requested data](/dl)`

---

## 2. Requesting Data<a id="requests"></a>

Below are listed the items you may request from the API.

* `url` - the link to the firmware on Apple's servers
* `md5sum` - the MD5sum of the IPSW
* `datefound` - the date the firmware was uploaded to Apple's Servers - formatted `Y-m-d`
* `filesize` - the filesize of the IPSW **in bytes**
* `device`/`name` - the user-friendly name of the device that the IPSW points to e.g. `iPod touch 5`
* `firmware`/`version` - the version of the IPSW file
* `buildid` - the BuildID of the firmware
* `identifier` - the user-unfriendly (but api friendly :P) identifier of the device e.g. `iPod5,1`
* `info.json` - all known information about the firmware (i.e. everything in this list) in json format
* `filename` - the filename of the IPSW
* `sha1sum` - the SHA1sum of the IPSW

---

## 3. Extras<a id="extras"></a>

* It is possible to download the IPSW when requesting the _URL only_ by adding `/dl` to the end of the URL (as shown above)
* A **JSON file** of all of the information provided by this API is found [here](http://api.ios.icj.me/firmwares.json) (`http://api.ios.icj.me/firmwares.json`) with a condensed version [here](http://api.ios.icj.me/firmwares.json/condensed) (`http://api.ios.icj.me/firmwares.json/condensed`). Do with it what you will.
* All data in this API updates automatically when a new firmware is released, usually within the minute.

---

## 4. Responses<a id="responses"></a>

The API responds with Status codes in the headers to provided information on the request you made.

* `400 Bad Request` - the request has not been completed due to a syntax or formatting error. Refer to this documentation.
* `404 Not found` - information not found, does not exist in database
* `300 Multiple Choices` - There are multiple pieces of data that have been returned to you. This is only when requesting by firmware, not buildid. The choices will be returned in a JSON format.
* `200 OK` - the data has been found and successfully returned to you. (this is the best one!)

--- 

## 5. Examples<a id="examples"></a>

Below are some example requests.

* `http://api.ios.icj.me/v2/iPod4,1/8B118/url`
* `http://api.ios.icj.me/v2/iPad1,1/8L1/datefound`
* `http://api.ios.icj.me/v2/iPad1,1/8L1/filesize`
* `http://api.ios.icj.me/v2/iPad1,1/8L1/url/dl`
* `http://api.ios.icj.me/v2/iPad3,1/latest/filename`
* `http://api.ios.icj.me/v2/iPad3,2/earliest/info.json`
* `http://api.ios.icj.me/v2/2c0dd880982f0f8e47dc3dadfb733ad7/url`
* `http://api.ios.icj.me/v2/2c0dd880982f0f8e47dc3dadfb733ad7/identifier`

---

## 6. Other Information<a id="other"></a>

* Note that this and all other parts of the API _do not_ return beta firmware or OTA update information.
* Please **assign your application a user agent** when you request a link. This will make it easier to track the API usage.
* There is a PHP Class and example for using the API on my [GitHub](https://github.com/cj123/fwlinks-api).

