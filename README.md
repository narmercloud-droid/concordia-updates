# concordia-updates

Update server for the Concordia Sunmi Terminal.

## Latest release

| Field | Value |
|-------|-------|
| Version | **1.3.2** (tag `v1.3.2`) |
| APK | [app-production-release.apk](https://github.com/narmercloud-droid/concordia-updates/releases/latest/download/app-production-release.apk) |
| Manifest | [latest.json](https://raw.githubusercontent.com/narmercloud-droid/concordia-updates/main/latest.json) |

## Install on Sunmi

1. Download `app-production-release.apk` from [Releases](https://github.com/narmercloud-droid/concordia-updates/releases/latest).
2. Copy to the device (USB, email, or cloud).
3. Enable **Install unknown apps** for your file manager.
4. Open the APK and install.

Package: `de.concordia.terminal`

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
- Backend: `https://concordia-backend-web.onrender.com`
