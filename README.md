# p2p voice

Encrypted peer-to-peer voice and text chat for up to 10 people, in a single HTML file.
No accounts, no sign-up, no server in the middle: audio and messages go directly between browsers.

**Open the app:** `https://<username>.github.io/p2p-chat/`

## How to use

1. Open an **invite link** someone sent you. Type your name once, and you join the room straight away. Allow the microphone when the browser asks.
2. Your rooms and friends are listed on the left. Click a room to join its voice chat; the bar at the bottom always shows where you are talking.
3. You can listen and write even without a microphone.

**Start your own room:** press **+ new** on the left, give it a name, save, then press **Invite** at the top of the room and send the link privately.

Works in Firefox, Chrome, Edge and Brave, on desktop and on phones. The interface is available in English and Polish.

## Features

- Voice and text chat for up to 10 people
- AI noise filter (RNNoise) for keyboard, fans and background noise, plus a noise gate
- Per-person volume, master volume, and muting people just for yourself
- Friends: add people from their card, then chat with them privately at any time and call them; messages to an offline friend are delivered when you are both online
- IRC-style commands (type `/help`), mentions, and optional soft mechanical sounds
- Room lock: only your friends can talk with you
- Simple mode for people who just want to talk
- Green, amber and cyan terminal themes

## Privacy and security

- **End-to-end encrypted.** Voice and chat use WebRTC encryption (DTLS-SRTP) with fresh keys for every connection. Nobody between the participants can listen in.
- **Second layer for chat.** Messages, names and invites are additionally encrypted with AES-256-GCM using a key derived from the room's invite. This layer does not rely on elliptic-curve key exchange, so recorded chat traffic stays protected even against future quantum computers, as long as the invite stays private. Voice uses only the WebRTC layer.
- **No server stores anything.** This page is only the app. Public Nostr relays are used to find each other, and they only see encrypted handshake messages.
- **Invite links are keys.** Anyone with a room's invite link can join that room. Send invites privately. The room part of the link (after `#`) is never sent to any server, including GitHub.
- **Friends.** Everyone has an account key stored in their browser. When you add someone as a friend you can compare the safety code with them once (for example by reading it aloud); the app then warns you if someone else uses their name.
- **IP addresses.** As with any direct connection, participants can see each other's IP address. Google and Cloudflare STUN servers help find a route and also see your IP address.
- **Your data stays in your browser:** name, account, friends, rooms and settings. Export your account in Settings to back it up or move it to another device. **Panic** in Settings wipes everything.

## Troubleshooting

- **Someone shows as "not connected to you"**: others reach them but your connection failed. This is usually the network (strict routers, mobile carriers, company Wi-Fi). Type `/diag` on both devices and compare.
- **No sound**: check that the person's level bar moves, that the browser tab is not muted, and the volume sliders. Open a person's card to see whether audio arrives (`↓ ↑ kbit/s`).
- **Microphone not working**: click the microphone or lock icon in the address bar and allow it, then use *Retry microphone* in Settings.
- **Everyone must use the same version.** Type `/diag` to see your version. After an update, everyone reloads the page.

## Self-hosting

The whole app is `index.html`. Put it on any static HTTPS host (GitHub Pages, Netlify, Cloudflare Pages) or open it as a local file. Phones need the hosted HTTPS version.

## Credits

- [Trystero](https://github.com/dmotz/trystero) 0.21.6 (MIT), with local patches for connection reliability
- [@noble/secp256k1](https://github.com/paulmillr/noble-secp256k1) 1.7.1 (MIT)
- [RNNoise](https://github.com/xiph/rnnoise) (BSD-3-Clause), WebAssembly build from [jitsi/rnnoise-wasm](https://github.com/jitsi/rnnoise-wasm)
