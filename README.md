# fridgenote-links

Static site backing the FridgeNote Android app. Public so GitHub Pages can
serve it; the app's own source lives in the private `fridgenote` repo.

- `.well-known/assetlinks.json` — Android App Links verification. Lists the
  `com.fridgenote` package and both signing certificates (release, and the
  container's debug key so sideloaded debug builds also open links).
- `join/` — the landing page a join link points at. It is a fallback: if the
  app is installed and verified, Android opens the app instead and this page
  is never seen.

Join links carry the fridge's encryption key **in the URL fragment**, after
the `#`. Fragments are never sent to a server, so neither GitHub nor any link
preview ever receives the key. It reaches only the phone that opens it.

If the app's signing certificate ever changes, update the fingerprints in
`assetlinks.json` or every link will silently stop opening the app.
