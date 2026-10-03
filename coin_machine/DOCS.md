# Coin Machine

Coin Machine is an AI deal analyst for coin flippers, collectors and dealers. It reads listings, works out melt value, fees and profit in code, and gives each deal a verdict. As an add-on it runs inside Home Assistant, so your hunts keep running with no browser open, and new BUY deals reach your phone as Home Assistant notifications.

It never bids, buys or messages anyone. Facebook Marketplace and similar sites stay manual: you capture a listing yourself and the app analyses it.

## Install

The app's image is private, so Home Assistant needs a read-only GitHub token to download it. You set this up once.

1. **Make the token.** On GitHub, open **Settings > Developer settings > Personal access tokens > Tokens (classic) > Generate new token (classic)**. Name it "Home Assistant", pick an expiry, tick only **read:packages**, and generate it. Copy the token; GitHub shows it once.
2. **Give it to Home Assistant.** Open **Settings > Add-ons > Add-on store**, open the menu (three dots, top right) and choose **Registries**. Add a registry with server `ghcr.io`, your GitHub user name, and the token as the password.
3. **Add the add-on listing.** In the same menu choose **Repositories**, add `https://github.com/dsdadsasdaaaaaaaa/coin-machine-ha` and close the dialog.
4. Find **Coin Machine** in the store (refresh the page if it does not appear) and choose **Install**.
5. On the **Configuration** tab, set the options below and choose **Save**.
6. On the **Info** tab, turn on **Watchdog**, then choose **Start**.
7. Open the **Log** tab and wait for the line that says the server is ready.

If the install fails with an "unauthorized" or "denied" error, the registry entry is missing or the token lacks **read:packages** or has expired. Fix it under **Registries** and install again.

Supported hardware: 64-bit Home Assistant systems (`amd64`, such as an Intel NUC or a virtual machine, and `aarch64`, such as a Raspberry Pi 4 or 5 running the 64-bit OS).

## Options

| Option | What it does |
|---|---|
| `access_password` | The password for signing in, at least 8 characters. If you leave it empty, the app creates one on its first start and prints it once in the **Log** tab. |
| `anthropic_api_key` | Your Claude API key from console.anthropic.com. Needed for photo analysis and deal reports. |
| `ebay_client_id`, `ebay_client_secret` | Your eBay developer keyset (App ID and Cert ID). Needed for hunts. |
| `ebay_environment` | `production` for real listings, `sandbox` for eBay's test site. |
| `pcgs_api_token` | Optional. PCGS certificate and price guide lookups. |
| `numista_api_key` | Optional. Numista catalogue estimates on world-coin deals, shown as estimates, never as sales. |
| `notify_service` | The notify service for your phone, such as `mobile_app_pixel_8`. New BUY deals are sent there. Empty means no phone alerts. |
| `publish_sensors` | Publish `sensor.coin_machine_*` entities for dashboards and automations. |
| `frame_ancestors` | Optional. Origins allowed to show the app inside a frame, such as `http://homeassistant.local:8123` for a dashboard webpage card. Empty blocks framing. |
| `public_url` | Optional. The address you open the app at, such as `http://homeassistant.local:3000`, used for links in phone alerts. Empty uses the address you last signed in from. |
| `timezone` | Optional. A time zone name such as `Europe/London`. Empty uses Home Assistant's time zone. |

Keys you leave empty here can be entered later in the app's **Settings** page instead. An option that is set always wins over a key saved in Settings.

The add-on log never shows your keys or password: each secret appears only as "set".

## First sign-in

1. On a laptop on the same network as Home Assistant, open `http://<home-assistant-address>:3000`, for example `http://homeassistant.local:3000` or `http://192.168.1.20:3000`. The **Open web UI** button on the add-on's Info tab opens the same page.
2. Enter the access password. If you did not set one, copy the generated password from the **Log** tab.
3. Open **Settings** in the app and check that your keys show as connected.

To change the password later, set `access_password`, save, and restart the add-on.

## Use it on your phone

1. Connect the phone to your home Wi-Fi and open `http://<home-assistant-address>:3000` in Safari (iPhone) or Chrome (Android).
2. Sign in.
3. Add it to your home screen: in Safari, **Share > Add to Home Screen**; in Chrome, the menu then **Add to Home screen**.

Away from home, use Home Assistant's own remote access (for example a VPN such as the Tailscale add-on). Do not forward port 3000 on your router: the app is served over plain HTTP and is meant for your home network.

## Phone notifications

1. Install the Home Assistant Companion app on your phone and sign in to your Home Assistant.
2. In Home Assistant, open **Developer tools > Actions** and type `notify.` to see your phone's service, such as `notify.mobile_app_pixel_8`.
3. Put the part after `notify.` (or the whole name) in `notify_service`, save, and restart the add-on.

When a scheduled hunt finds a new BUY deal, the phone gets a notification. Hunts need the eBay keys.

## Backups

The add-on keeps everything in its own data folder: the database, uploaded photos and the app's settings. Home Assistant backups include that folder, so a normal Home Assistant backup (**Settings > System > Backups**) saves your deals, positions, hunts and keys. The add-on stops for a few seconds while a backup runs so the database is copied in a consistent state, then starts again.

Restoring a Home Assistant backup that includes the add-on brings everything back.

## Troubleshooting

- **Install fails with "unauthorized" or "denied".** See the end of the Install section: the `ghcr.io` registry entry or its token is missing or expired.
- **The add-on stops right after starting.** Read the **Log** tab. A line starting with "Coin Machine cannot start" says which option to fix.
- **The page does not load on the phone.** Check the phone is on the home Wi-Fi, not mobile data, and that the address uses port 3000.
- **No phone notifications.** Check `notify_service` against **Developer tools > Actions**, and that hunts are running (the app's Hunts page shows the last run).
