# astrolabe-updates

Public update channel for the **Astrolabe Method** Android app (a private project). This repository is public on
purpose, so phones can fetch updates without credentials. It holds **only**:

- `channels/stable.json`, `channels/beta.json`: the update manifests, each with a detached Ed25519 signature (`.sig`, base64).
- Releases:
  - `web-<version>`: signed, minified web bundles (`.zip` + `.zip.sig`).
  - `app-<versionCode>`: release-signed APKs (`.apk` + `.apk.sig`).
  - `assets`: large, rarely changing files (hand-tracking model and WASM, star catalogue, ephemeris chunks, pdf.js
    decoders), each named by its SHA-256 and listed by hash in the signed bundles.

It contains no source code, no books and no private data. The app checks every manifest, bundle and APK against an
Ed25519 public key built into the app, and rejects anything else, including anything modified in this repository.

## Licenses and credits

Each bundle carries `NOTICES.txt` and `sky/STARS-CREDITS.txt`. In short:

- The star catalogue is an adaptation of the **HYG Database v4.1** by David Nash (astronexus), licensed **CC BY-SA 4.0**.
  The packed file (`sky/hyg41.stars`, also in the `assets` release) is shared under the same license.
- Constellation figures come from d3-celestial (© 2015 Olaf Frohn, BSD-3-Clause).
- Star names are from the IAU WGSN.
- Libraries: MediaPipe and the hand_landmarker model (Apache-2.0), pdf.js (Apache-2.0), astronomy-engine (MIT),
  three.js (MIT) and Capacitor (MIT).

The app's own compiled code is published here only as a build artifact. It is not open-source licensed: all rights
are reserved.
