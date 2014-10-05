Version 2.1 Changelog
=====================

## Global

### Headers
* **Content-MD5** is now base64 encoded, as it should be, and now called "Content-Md5" due to `net/http` restrictions in golang


### Responses
* **info.json requests** always return an array
* removed `id` from all responses
* all date responses are in **RFC3339**
* all uncondensed JSON responses are now indented with tabs, not spaces
* in JSON responses, `datefound` has been renamed to `uploaddate` and will always be shown. an extra field, `releasedate` will be shown if it is known (both RFC3339)

* * *

## firmwares.json

* device info is first now, not that it should make any difference if you're parsing it properly :P
* `itunes` has been renamed to `iTunes`
* added `releasedate` to `iTunes` responses.
* firmware.`filesize` has been renamed to firmware.`size` is now an _int_, not a _string_. 
* device.`cpid` and device.`bdid` are also _int_s instead of strings
* firmware.`signed` (shsh signing status (_boolean_)) is now shown for firmwares.
* all json responses (e.g. `info.json`) are now unified with firmwares.json (i.e. the responses are the same details)

Full JSON types and layouts here (taken directly from the code):

<pre class="code" style="width: auto; min-width: auto;"><code data-language="go">
/** firmwares.json types **/
type Device struct {
	Name        string      `json:"name"`
	BoardConfig string      `json:"BoardConfig"`
	Platform    string      `json:"platform"`
	CPID        int         `json:"cpid"`
	BDID        int         `json:"bdid"`
	Firmwares   []*Firmware `json:"firmwares"`
}

type Firmware struct {
	Identifier  string `json:"identifier,omitempty"`
	Version     string `json:"version"`
	Device      string `json:"device,omitempty"`
	BuildID     string `json:"buildid"`
	SHA1        string `json:"sha1sum"`
	MD5         string `json:"md5sum"`
	Size        int    `json:"size"`
	ReleaseDate string `json:"releasedate,omitempty"`
	UploadDate  string `json:"uploaddate"`
	URL         string `json:"url"`
	Signed      bool   `json:"signed"`
	Filename    string `json:"filename"`
}

type iTunes struct {
	Platform        string `json:"platform,omitempty"`
	Version         string `json:"version"`
	UploadDate      string `json:"uploaddate"`
	URL             string `json:"url"`
	SixtyFourBitURL string `json:"64biturl,omitempty"`
	ReleaseDate     string `json:"releasedate,omitempty"`
}
</code></pre>

## firmware requests

* removed request mapping, so the following requests **do not** exist (alias => actual):
	<pre class="code" style="width: auto; min-width: auto;"><code data-language="go">
		/** removed aliases **/ 
		"firmware":    "version",
		"date":        "datefound",
		"releasedate": "datefound",
		"info.json":   "info",
		"sha1":        "sha1sum",
		"md5":         "md5sum",
		"device":      "name",
	</code></pre>

	however, `releasedate` is repurposed to give the date the firmware was released on (if it exists) or return a 404 error if it does not. See documentation for valid requests.
* `uploaddate` added. This is the date the firmware was uploaded to the server. This is more reliable than `releasedate` for older firmwares.
* removed `datefound` tag. see above for more improved naming of tags
* `signed` is now a boolean
* removed `disabled` field in info.json -> if it were true, the firmware would not be shown anyway...
* filename requests now always return the true filename, based from the URL of the IPSW. This means for some AppleTV versions things may seem different because of Apple's strange versioning.

* * * 

## iTunes

* **platform aliases removed**. Now use `win` for Windows and `osx` for Mac OS X.

* * *

## redsn0w

* **discontinued as of v2.1**. With a lack of new releases, it makes no sense to keep updating the API. Use [v2/redsn0w](/docs/2/redsn0w) instead.

* * *

## PwnageTool

* **discontinued as of v2.1**. With a lack of new releases, it makes no sense to keep updating the API. Use [v2/PwnageTool](/docs/2/PwnageTool) instead.

* * *

Contact me if you wish to query any of these changes.
