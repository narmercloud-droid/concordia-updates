# concordia-updates

Update server for the Concordia Sunmi Terminal.

## How auto-update works

Terminals on **v1.6.34+** check this repo over Wi-Fi:

1. App reads [`latest.json`](https://raw.githubusercontent.com/narmercloud-droid/concordia-updates/main/latest.json)
2. If `versionCode` is newer than the installed app, it downloads the APK
3. Android shows the install screen once (tap Install) — no PC/USB needed

**First time only:** install a **release-signed** build (v1.6.43+). Debug-signed installs cannot update over a release-signed APK (or the other way around) without uninstalling first.

## Publish a new version

From `concordia-terminal-ui` (requires `android/keystore.properties` + release JKS):

```powershell
powershell -ExecutionPolicy Bypass -File scripts/publish-update.ps1 -Push
```

That builds the release APK, writes `latest.json` / `checksum.sha256` / `apk/`, commits this repo, and creates the GitHub Release.

## Latest release

| Field | Value |
|-------|-------|
| Version | **1.6.43** (tag `v1.6.43`) |
| APK | [app-production-release.apk](https://cdn.jsdelivr.net/gh/narmercloud-droid/concordia-updates@main/apk/app-production-release.apk) |
| Manifest | [latest.json](https://raw.githubusercontent.com/narmercloud-droid/concordia-updates/main/latest.json) |

## Manual install (old terminals / first update)

1. Download `app-production-release.apk` from [Releases](https://github.com/narmercloud-droid/concordia-updates/releases/latest).
2. On the Sunmi, open the APK (browser/Files) and install.
3. Enable **Install unknown apps** for Concordia Terminal if asked.
4. If Play Protect warns on a dedicated kitchen device, turn off scanning for this POS tablet after confirming the APK checksum.

Package: `de.concordia.terminal`

## What's new in 1.6.43

- Release-signed APK (stops Android Debug signing, which Play Protect treated as harmful)
- Keep scheduled orders on the terminal board through the day they are due, even if placed earlier
- Same Wi-Fi auto-update channel; future OTAs require the same release certificate

## What's new in 1.6.36

- Bukarest-style kitchen UX: shared timers, scheduled-time adjuster, clearer incoming-order flow
- Restore ZCS / Kingtop printer support alongside Sunmi
- Ticket print settings and auto-print hardening for branch terminals

## What's new in 1.6.35

- Print Klingel/Etage delivery hints as Anmerkungen, not as extra address lines

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
