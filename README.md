# Signature HTML Generator

A local browser-based generator for Thunderbird-compatible HTML email signatures.

- No install required
- No backend
- No build step
- Runs locally in a browser
- Generates Thunderbird-friendly HTML using tables and inline styles
- Supports base64 embedded logos
- Supports per-field typography settings
- Supports optional clickable social buttons
- Supports JSON profiles

## Usage

1. Open `index.html` in a browser.
2. Optionally load a JSON profile from `profiles/`.
3. Select a logo.
4. Fill in the signature fields.
5. Adjust typography field by field.
6. Optionally enable social buttons and enter profile URLs.
7. Click **Preview**.
8. Download `signature-base64.html`.
9. In Thunderbird, select that file as the account signature.

## Why base64?

`signature-base64.html` embeds the logo directly in the HTML file. This avoids fragile local paths on Windows/Linux and is usually the most reliable option for Thunderbird.

## Files

```text
index.html              Main generator
profiles/example.json   Example profile
docs/                   Additional notes
LICENSE                 License
```

## Compatibility notes

Email clients are restrictive. This generator intentionally uses:

- HTML tables
- inline CSS
- no JavaScript in generated signatures
- no external CSS
- no border radius on the logo
- fixed logo width with automatic height

## Development

There is no build step. Edit `index.html` directly.

A quick syntax check can be run with Node.js if available:

```bash
node -e "const fs=require('fs'); const s=fs.readFileSync('index.html','utf8'); new Function(s.match(/<script>([\\s\\S]*)<\\/script>/)[1]); console.log('OK')"
```

## License

MIT

## Save a profile

Use **Sauver ce profil en JSON**, enter a profile name, and the browser downloads `<profile-name>.json`.
