# YouTube Auto-hide Header

A Firefox and Chrome extension that hides the YouTube header (logo, search bar and top buttons) and brings it back when you hover the top edge of the page.

Built for people who use their monitor in portrait orientation or on a short screen, where the fixed header takes up space the content needs.

## How it works

- The header stays hidden, leaving only a 6px strip at the top of the page.
- Hovering that strip slides the header into view.
- While the search box is focused, the header stays visible.
- The blank space the header used to occupy is removed.

The extension is CSS only (`content.css`), with no scripts and no extra permissions. It does not collect or transmit any data and runs only on `youtube.com`.

## Structure

```
.
├── manifest.json   # Manifest V3, works on Firefox and Chrome
├── content.css     # Rules that hide and reveal the header
└── README.md
```

## Installation

### Chrome / Edge / Brave

1. Download or clone this repository.
2. Open `chrome://extensions` and turn on **Developer mode**.
3. Click **Load unpacked** and select the project folder.

The extension stays installed after you close the browser. Chrome may show a warning about developer mode extensions on startup.

### Firefox

**Temporary** (removed when the browser closes):

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on**.
3. Select the project's `manifest.json`.

**Permanent:** Firefox only keeps extensions signed by Mozilla.

1. Zip `manifest.json` and `content.css` at the root of a `.zip` (the files themselves, with no folder inside).
2. Upload it at [addons.mozilla.org/developers](https://addons.mozilla.org/developers/) and choose **On your own** (unlisted distribution).
3. Download the signed `.xpi` and open it in Firefox.

Alternatively, on Firefox Developer Edition or Nightly you can set `xpinstall.signatures.required` to `false` in `about:config` and install the package unsigned.

The extension ID for Firefox is in `browser_specific_settings.gecko.id` in `manifest.json`.

## Customization

Everything lives in `content.css`:

| What to change | Where |
| --- | --- |
| Size of the strip that reveals the header | `6px` in `translateY(calc(-100% + 6px))` |
| Delay before hiding again | last value of `transition: transform 0.2s ease 0.25s` |
| Animation speed | first value (`0.2s`) of the same `transition` |

## Limitations

YouTube changes its HTML often. If the header stops hiding, or a blank gap shows up at the top, the selectors (`#masthead-container`, `ytd-page-manager`) probably need updating. Open an issue noting the affected page (home, video, search).

## License

Set the project license here (for example, MIT).
