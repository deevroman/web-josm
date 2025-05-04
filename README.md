## JOSM in Browser!

Demo: https://deevroman.github.io/web-josm

Powered by https://cheerpj.com

## Authorization

You must manually enter the OAuth2 token in the JOSM settings.
1. `Edit`→`Preferences`→`Expert Mode`
2. `OSM Server`→`Authorize now (Manual)`

The easiest way to get it is to open [osm.org/id](https://osm.org/id) and run in the browser console: `document.querySelector("#id-container").getAttribute("data-token")`

## Usage

Offline mode is enabled by default for josm.openstreetmap.de. Due to the limitations of CORS, access to it is limited, so you must first install and enable [this extension](https://webextension.org/listing/access-control.html). Only then can you disable offline mode. (`File`→`Offline Mode`→`JOSM Website`). Don't forget to turn off the extension after exiting JOSM.

## What for?

Just for fun. Now you can replace the iD editor on the osm website with JOSM with [my userscript](https://github.com/deevroman/better-osm-org/)

![demo](demo.webp)


## How it's done

Cheerpj allows you to run applications that require Java 8 or Java 11. However, I was unable to patch JOSM to make JOSM work with Java 11 due to some internal errors.

So I took the latest JOSM that runs on Java 8 ([#18984](https://josm.openstreetmap.de/log/josm?action=stop_on_copy&mode=stop_on_copy&rev=&stop_rev=18984&limit=700&verbose=on)) and [cherry-picked](https://github.com/deevroman/josm/commits/master/) the commits that are needed to support manual authorization via OAuth 2. And I [built](https://github.com/deevroman/josm/releases/tag/19367) a jar using GitHub Actions, which is located in this repository.

## Known issues

- It is unlikely that all plugins will work
- You need to install an extension to bypass CORS (browsers block josm.openstreetmap.de)
- ESRI tiles are unstable for some reason
- Remote control is not working
- It follows that authorization works only by token
- Sudden random error messages
- Some pop-up windows don't show the first time
