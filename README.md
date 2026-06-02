# Sumiran — your shorts, in order

A tiny web app that plays *your* list of YouTube Shorts one after another, and
nothing else. Lists are saved on your device, with multiple playlists, shuffle,
and loop. It installs to your phone's home screen like a real app.

## Files
```
index.html              the whole app
manifest.webmanifest    makes it installable
sw.js                   service worker (offline shell + install)
icon-192.png            app icons
icon-512.png
icon-maskable-512.png
apple-touch-icon.png
favicon-32.png
```
Everything is static — no build step, no server code.

## Deploy

### Netlify (drag & drop, ~30 seconds)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get a live HTTPS URL instantly. Done.

(To get a nicer URL or auto-updates, push the folder to a GitHub repo and
"Add new site → Import an existing project" instead.)

### Cloudflare Pages
1. Go to the Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages**.
2. Choose **Upload assets** (direct upload) and drop this folder, **or** connect
   a GitHub repo.
3. Build command: *(leave empty)*. Output directory: `/` (the folder root).
4. Deploy → you get an HTTPS URL.

HTTPS matters: the "install to home screen" feature and the service worker only
work over https:// (both hosts above give you that automatically). Opening
`index.html` directly from your file system works for testing but won't be
installable.

## Use it
- Tap **Edit** to paste your Shorts links (one per line). Saved automatically.
- **Play** runs the list top to bottom; the next Short auto-starts when one ends.
- The chip at the top switches between **playlists**; **+ New playlist** adds more.
- **Shuffle** and **Loop** toggle along the bottom.
- On a phone: open the URL, then "Add to Home Screen" for an app icon.

## Notes
- Uses YouTube's official embedded player (this is the allowed way — no
  downloading or re-hosting of videos).
- A few videos have embedding disabled by their uploader; those are skipped.
- It shows the standard YouTube player, not the swipe-up Shorts interface (that
  UI is YouTube's own and isn't available to outside apps).
