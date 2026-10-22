# QuotaTray Resource Packs

Public distribution point for [QuotaTray](https://payhip.com/b/o7RZ1)
resource packs — the declarative tool packs the native QuotaTray app
fetches from Settings → Tool Library.

- `manifest.json` — the signed catalog. The app verifies its ed25519
  signature (keyId `quotatray-packs-2026`) against a public key pinned
  in the app binary before trusting anything in it, then verifies each
  pack file against the sha256 recorded in the manifest.
- `packs/<id>-<version>.json` — immutable pack files. A published file
  never changes; an updated pack ships under a new version (and file
  name) and the manifest is re-signed to point at it.

Clients fetch the manifest from
`https://raw.githubusercontent.com/dylanXM/quotatray-resource-packs/main/manifest.json`
and resolve each pack's `file` path relative to it.

Publishing is done with `resource-packs/tools/build_manifest.py` in the
(private) `quotatray-native` repository, which assembles and signs the
manifest with the offline release key; the output is committed here.
