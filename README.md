# concordia-updates

Update server for the Concordia Sunmi Terminal.

## How auto-update works

Terminals on **v1.6.34+** check this repo over Wi‑Fi:

1. App reads [`latest.json`](https://raw.githubusercontent.com/narmercloud-droid/concordia-updates/main/latest.json)
2. If `versionCode` is newer than the installed app, it downloads the APK
3. Android shows the install screen once (tap Install) — no PC/USB needed

**First time only:** install a build that includes auto-update (v1.6.34+). After that, publishing here is enough.

## Publish a new version

From `concordia-terminal-ui`:

```powershell
npm run apk:publish
```

Then:

1. Create a GitHub Release in this repo (`vX.Y.Z`)
2. Upload the built APK as **`app-production-release.apk`**
3. Commit & push updated `latest.json` + `checksum.sha256`

## Latest release

| Field | Value |
|-------|-------|
| Version | **1.6.28** (tag `v1.6.28`) |
| APK | [app-production-release.apk](https://github.com/narmercloud-droid/concordia-updates/releases/latest/download/app-production-release.apk) |
| Manifest | [latest.json](https://raw.githubusercontent.com/narmercloud-droid/concordia-updates/main/latest.json) |

## Manual install (old terminals / first update)

1. Download `app-production-release.apk` from [Releases](https://github.com/narmercloud-droid/concordia-updates/releases/latest).
2. On the Sunmi, open the APK (browser/Files) and install.
3. Enable **Install unknown apps** if asked.

Package: `de.concordia.terminal`


## What's new in 1.6.28

- Sunmi V2s only — removed legacy Kingtop Z91 / ZCS printer support
- Confirm orders before printing with rollback on API failure
- Handle `order:rejected` realtime events

## What's new in 1.6.27

- Confirm orders before printing with rollback on API failure
- Handle `order:rejected` realtime events on the terminal
- Improved login error messages from wrapped API responses

## What's new in 1.3.3

- Fix pause orders (backend + terminal)
- Improved Kingtop Z91 printer SDK integration (correct Z91 API)
- App returns to foreground 3 seconds after Home button
- Smaller, optimized release APK (minify + shrink)

## What's new in 1.3.2

- Full-screen incoming order alert with louder repeating tone until accept/decline
- Pause orders: clear confirmation in menu, status indicator, and header badge
- No countdown timer on finished/delivered orders
- Removed redundant "Nur heutige Bestellungen · Live aktiv" subtitle

## What's new in 1.3.1

- Fixed order status updates (Unterwegs / Geliefert buttons)
- Kingtop Z91 built-in printer support (Kempen terminal)
- Driver QR scan auto-moves order to Unterwegs
- Faster app when live socket is connected
- Clearer German error messages for failed updates

## What's new in 1.3.0

- Merged **In Arbeit** tab: new orders stay on top until accepted/rejected
- Louder repeating alert for unhandled orders
- Delivery countdown timer on order cards
- Side menu: pause orders, day report, language (DE / AR)
- Hardware back navigates inside app (does not exit)
- Move orders between In Arbeit → Unterwegs → Erledigt
- Improved Sunmi printer binding and error messages
- Screen stays on, fullscreen kiosk-style UI
- Production API: `https://api.concordiapizza.de` (Render service: `concordia-backend-eu`)
