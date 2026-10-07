# No Autoplay, Thanks!

A lightweight browser extension that helps stop unwanted autoplaying video and audio while keeping normal manual playback working.

**No Autoplay, Thanks!** was made for one simple reason: if I want to watch or hear something, I can press Play myself.

The extension focuses on reducing unwanted autoplay without trying to become an ad blocker, privacy suite, media manager, or giant browser-control dashboard.

No ads. No analytics. No tracking. No remote code.

![No Autoplay, Thanks!](no-autoplay-videos-and-audio.png)

## What It Does

- Removes autoplay from normal video and audio elements where possible
- Pauses media that starts without a recent user action
- Keeps normal manual playback working
- Includes a global **Block autoplay** switch
- Lets you **Allow this site** when autoplay is useful
- Can optionally **Allow muted autoplay**
- Can cautiously **Reduce preloading**
- Stores settings using Chrome extension storage
- Runs locally in the browser
- Uses Manifest V3
- Avoids aggressive blocking techniques that can break complex websites

The goal is not to win a technical war against every media player ever created.

The goal is simpler: fewer surprise videos, fewer unwanted sounds, less pointless media loading, and a calmer browser.

## How It Works

The extension listens for normal video and audio playback events on supported web pages.

When media starts, it checks whether playback appears to follow a recent user action. If not, and autoplay blocking is enabled for that site, the extension can pause the media and remove autoplay flags where possible.

Manual playback is intentionally preserved. If you click or tap a player yourself, the extension treats that as a user-requested action and allows playback.

The current implementation is deliberately compatibility-first. Earlier experiments used more aggressive techniques, but modern websites and custom players can become unstable when extensions interfere too deeply with their media logic.

For that reason, the extension favors lighter event-based handling over constant heavy page scanning or invasive player modification.

## Settings

### Block autoplay

The global on/off switch.

### Allow this site

Allows autoplay on the current website. The rule is stored by hostname.

### Allow muted autoplay

Lets muted media autoplay if you do not mind silent videos starting automatically.

### Reduce preloading

Can cautiously reduce media preload behavior to `metadata` where appropriate.

## Compatibility First

No Autoplay, Thanks! intentionally avoids several aggressive techniques that created compatibility problems on some modern websites.

The current build does not rely on:

- Full-page MutationObserver scanning
- Main-world `HTMLMediaElement.play()` overrides
- Iframe URL rewriting
- Aggressive iframe permission rewriting
- Shadow DOM crawling
- Continuous startup scanning
- Broad source-attribute monitoring
- Web Audio API blocking

The extension also avoids injecting into several heavy AI chatbot and web-app domains where autoplay blocking is generally unnecessary and content-script injection can add unwanted overhead.

The philosophy is simple: an autoplay blocker should not become another thing that makes websites slow or unstable.

## Privacy

No Autoplay, Thanks! does not:

- Collect personal data
- Track browsing history
- Use analytics
- Show ads
- Send browsing data to a remote server
- Load remote executable code
- Require an account
- Require a subscription

Settings are stored through Chrome extension storage so your choices can be remembered.

## Permissions

### `activeTab`

Used by the popup to identify the current website, manage **Allow this site**, and reload the current tab when requested after changing settings.

### `storage`

Used to remember the extension settings and allowed websites.

### Website access

The content script runs on supported HTTP and HTTPS pages so it can detect and control media playback locally.

Browser-protected pages such as `chrome://` pages and the Chrome Web Store cannot be controlled by normal extensions.

## Known Limitations

No autoplay blocker can guarantee perfect behavior on every website.

Some sites use custom JavaScript players, nested or cross-origin frames, closed shadow DOM, non-standard media systems, delayed player injection, or repeated script-triggered playback.

The extension is intentionally conservative because breaking fewer websites is more useful than winning every autoplay battle.

## Project Page

More information, background, screenshots, and support are available on the IT SUCKS! website:

[Browser Extension to Stop Autoplay Videos and Audio](https://www.itsucks.fyi/browser-extension-to-stop-autoplay-videos-and-audio/)

## Installation

### Chrome / Chromium

For development or manual installation:

1. Download or clone this repository.
2. Open `chrome://extensions/`.
3. Enable **Developer mode**.
4. Click **Load unpacked**.
5. Select the extension folder containing `manifest.json`.

## Changelog

### 1.2.2

- Refined the popup and package for the current Chrome/Chromium build.
- Redesigned the **Leave a Tip** area using the final compact 120 × 32px treatment.
- Cleaned up popup spacing, CSS, footer placement, and small interface details.
- Improved startup and settings handling.
- Improved muted-autoplay behavior and keyboard/manual-playback handling.
- Improved save-error handling in the popup.
- Preserved the cautious preload behavior.
- Kept protected-page handling and existing site exclusions intact.
- Updated documentation.
- Added no new dependencies and did not reintroduce aggressive autoplay-blocking techniques.

### 1.2.1

- Added and refined the optional **Leave a Tip** block.
- Added the PayPal tip link.
- Refined popup hover styling and footer placement.
- Cleaned the packaged extension and removed stale `_metadata`.
- Preserved the existing lightweight autoplay-blocking behavior.

### 1.2.0

- Moved to the current lightweight, compatibility-first autoplay-blocking approach.
- Switched to safer media-event handling instead of aggressive page-wide monitoring.
- Preserved manual video and audio playback after recent user interaction.
- Kept the four main controls: **Block autoplay**, **Allow this site**, **Allow muted autoplay**, and **Reduce preloading**.
- Changed content-script timing to `document_idle`.
- Avoided `all_frames` injection in the Chrome build.
- Removed heavier experimental techniques including full-page MutationObserver monitoring, iframe rewriting, shadow DOM scanning, main-world `play()` overriding, and aggressive startup scanning.
- Added exclusions for selected heavy AI chatbot and web-app domains for compatibility.
- Kept the extension local, lightweight, ad-free, analytics-free, tracking-free, and free of remote code.

### Earlier Development

Earlier builds established the basic extension concept and tested more aggressive approaches to autoplay blocking.

Those experiments were useful, but some techniques caused unnecessary compatibility problems on complex websites. The project eventually moved toward the simpler event-based approach used by the current version.

## Development History

Development of **No Autoplay, Thanks!** began on May 26, 2026 as part of the IT SUCKS! project.

The extension was approved for the Chrome Web Store on August 20, 2026.

Version 1.2.2 was completed at the end of September 2026, with the focus remaining on compatibility, privacy, and keeping the extension deliberately small.

## Download

The easiest way to install **No Autoplay, Thanks!** is through the Chrome Web Store:

[**Install No Autoplay, Thanks! from the Chrome Web Store**](https://chromewebstore.google.com/detail/no-autoplay-thanks/bpoabmnbooiigclffibbgpfioheofdpf)

Installation is handled directly by Chrome, and updates are delivered automatically through the Chrome Web Store.

## About IT SUCKS!

No Autoplay, Thanks! is part of the **IT SUCKS!** project.

IT SUCKS! builds small, focused tools without unnecessary advertising, analytics, telemetry, account systems, or cloud machinery.

If I want to watch a video, I can press Play.

Giving users no real choice is not user-friendly.

**It sucks.**
