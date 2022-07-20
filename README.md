# p2pkit

Browserified versions of these libraries:

- <https://github.com/feross/simple-peer>
- <https://github.com/subins2000/simple-peer-files>
- <https://github.com/subins2000/p2pt>


## Usage

Load via HTML script tag:

```html
<script
  src="https://cdn.jsdelivr.net/npm/p2pkit@0.0.0-2/dist/index.js"
  integrity="sha256-IBqKNNdZBkvlyBDTBnPO57idR/RhhMygjQ59d9MsNZ4="
  crossorigin="anonymous"
></script>
```

This gives you 3 things:

```js
p2pkit.SimplePeer
p2pkit.SimplePeerFiles
p2pkit.P2PT
```

Use em!

```js
// Create an announce list
// Go to https://instant.io/ and run this in JS Console: `WEBTORRENT_ANNOUNCE`
const trackersAnnounceURLs = [
  'wss://tracker.btorrent.xyz',
  'wss://tracker.openwebtorrent.com',
]

// Create a room
const roomId = 'something-unique'
const p2pt = new p2pkit.P2PT(
  trackersAnnounceURLs,
  roomId,
)

p2pt.on('trackerwarning', (error, stats) => {
  // ...
})
p2pt.on('trackerconnect', (tracker, stats) => {
  // ...
})
p2pt.on('peerconnect', (peer) => {
  // ...
  p2pt.send(peer, { message: 'meow' })
})
p2pt.on('peerclose', (peer) => {
  // ...
})
p2pt.on('msg', (peer, message) => {
  // ...
})
p2pt.start()
```

## Example apps

- <https://github.com/dtinth/pipe>
