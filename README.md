# Google Maps API Scanner
Used for determining whether a leaked/found Google Maps API Key is vulnerable to unauthorized access by other applications or not.  

***[Blog Post #1 - Unauthorized Google Maps API Key Usage Cases, and Why You Need to Care](https://medium.com/bugbountywriteup/unauthorized-google-maps-api-key-usage-cases-and-why-you-need-to-care-1ccb28bf21e)***

***[Blog Post #2 - Google Maps API (Not the Key) Bugs That I Found Over the Years](https://medium.com/bugbountywriteup/google-maps-api-not-the-key-bugs-that-i-found-over-the-years-781840fc82aa)***

***Please note that most of the bug bounty platforms marking this vulnerability type as informational/low impact. So please make sure that the platform or program is accepting this kind of issues before reporting.***

***Usage:***

- Either download the Python file directly or install it with **pip** or **pipx**.
- Script will return `API key is vulnerable for XXX API!` message and the PoC link/code if determines any unauthorized access within this API key within any API's.

```
pipx install git+https://github.com/ozguralp/gmapsapiscanner
gmapapiscanner --api-key KEY
```



***Checked APIs:***
- Staticmap API
- Streetview API
- <s>Embed (Basic-Free) API</s> (No longer checked since it is completely free.)
- <s>Embed (Advanced-Paid) API</s> (No longer checked since it is completely free.)
- Directions API
- Geocode API
- Distance Matrix API
- Find Place From Text API
- Autocomplete API
- Elevation API
- Timezone API
- Roads API
- Geolocation API
- Route to Traveled API
- Speed Limit-Roads API
- Place Details API
- Nearby Search-Places API
- Text Search-Places API
- Places Photo API
- <s>Playable Locations API</s> (API is deprecated.)
- FCM API
- Custom Search API

***Semi-Auto Checked APIs:***
- JavaScript API

***Notes:***
- Because JavaScript API needs manual confirmation from a web browser directly, only file is created via the script for manual checks/confirmation.
- For Staticmap, Streetview and Embed API's, if used from another domain instead of just testing from browser; whether referer checks are enabled or not on the server-side for the key, script still could return it as vulnerable due to a server-side vulnerability. If you cannot reproduce the vulnerability via browser while the script says so, please read the ***Blog Post #2*** for more information & a better understanding about what is going on. 
- If you find any Google Maps API's which are not mentioned in this document/script, create an issue with details so I can also add them.
- Special thanks to [Yatin](https://twitter.com/ysirpaul) for his contributions on both discovery of additional API's & cost information!


## Docker
To run this script in a Dockerized Alpine Linux environment, use the following commands:
```
docker build -t google_maps_api_scanner .
docker run --rm -v $(pwd):/opt/html -i docker.io/library/google_maps_api_scanner <api key>
```
