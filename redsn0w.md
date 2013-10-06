## redsn0w

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

* `[Operating System]` - the Operating System you wish to request
* `[version]` - redsn0w version
* `[request]` - the thing you're requesting

The request URL is formatted as so:

`http://api.ios.icj.me/v2/redsn0w/[Operating System]/[version]/[request](/dl)`

Note that `[version]` can be replaced with "latest" to find the latest version.

## 2. Requesting Data<a id="requests"></a>

Below are listed the items you may request from the API.

* `url` - the link to the redsn0w release
* `datefound` - the date that the version of redsn0w was released formatted `Y-m-d`
* `version` - the version of redsn0w
* `info.json` - all known information about the redsn0w release (i.e. everything in this list) in json format
* `filename` - the filename of the redsn0w zip file

---

## 3. Extras<a id="extras"></a>

* It is possible to download the file when requesting the _URL only_ by adding `/dl` to the end of the URL (as shown above)

---

## 4. Responses<a id="responses"></a>

The API responds with Status codes in the headers to provided information on the request you made.

* `400 Bad Request` - the request has not been completed due to a syntax or formatting error. Refer to this documentation.
* `404 Not found` - information not found, does not exist in database
* `200 OK` - the data has been found and successfully returned to you. (this is the best one!)

--- 

## 5. Examples<a id="examples"></a>

Below are some example requests.

* `http://api.ios.icj.me/v2/redsn0w/Windows/latest/url`
* `http://api.ios.icj.me/v2/redsn0w/MacOSX/0.9.14b1/datefound`

---

## 6. Other Information<a id="other"></a>

* Please **assign your application a user agent** when you request a link. This will make it easier to track the API usage.

