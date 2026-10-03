# Coin Machine

Coin Machine is an AI deal analyst for coin flippers, collectors and dealers. It reads listings, works out melt value, fees and profit in code, and gives each deal a verdict. As an add-on it runs inside Home Assistant, so your hunts keep running with no browser open, and new BUY deals reach your phone as Home Assistant notifications.

It never bids, buys or messages anyone. Facebook Marketplace and similar sites stay manual: you capture a listing yourself and the app analyses it.

## Install

The app's image is private, so Home Assistant needs a read-only GitHub token to download it. You set this up once.

1. [Create a GitHub token](https://github.com/settings/tokens/new?scopes=read:packages&description=Home%20Assistant%20Coin%20Machine). Only **read:packages** is ticked: pick an expiry, choose **Generate token** and copy it (GitHub shows it once).
2. [Open the add-on store](https://my.home-assistant.io/redirect/supervisor_store/), then the menu (three dots, top right) > **Registries**. Add server `ghcr.io`, your GitHub user name, and the token as the password.
3. [Add the Coin Machine repository to Home Assistant](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fdsdadsasdaaaaaaaa%2Fcoin-machine-ha) and confirm.
4. [Open the Coin Machine add-on](https://my.home-assistant.io/redirect/supervisor_addon/?addon=53ba94f3_coin_machine&repository_url=https%3A%2F%2Fgithub.com%2Fdsdadsasdaaaaaaaa%2Fcoin-machine-ha) and choose **Install**.
5. Turn on **Watchdog** and choose **Start**.
6. Copy the access password from the **Log** tab, choose **Open web UI** and sign in.

Nothing on the **Configuration** tab is required. A Reddit hunt is added on the first start and brings in live sale posts every 30 minutes with no keys. To go further, paste keys in the app's **Settings** page (or on the Configuration tab): an [Anthropic API key](https://console.anthropic.com/settings/keys) for photo analysis and deal reports, and [eBay keys](https://developer.ebay.com/my/keys) for eBay hunts.

If the install fails with an "unauthorized" or "denied" error, the registry entry is missing or the token lacks **read:packages** or has expired. Fix it under **Registries** and install again.

Supported hardware: 64-bit Home Assistant systems (`amd64`, such as an Intel NUC or a virtual machine, and `aarch64`, such as a Raspberry Pi 4 or 5 running the 64-bit OS).

## Options

You can leave every option as it is.

| Option | What it does |
|---|---|
| `access_password` | The password for signing in, at least 8 characters. If you leave it empty, the app creates one on its first start and shows it in the **Log** tab on every start. |
| `anthropic_api_key` | Your Claude API key, from the [Anthropic console](https://console.anthropic.com/settings/keys). Needed for photo analysis and deal reports. |
| `ebay_client_id`, `ebay_client_secret` | Your eBay developer keyset (App ID and Cert ID), from [eBay's developer keys page](https://developer.ebay.com/my/keys). Needed for eBay hunts; the Reddit hunt needs no keys. |
| `ebay_environment` | `production` for real listings, `sandbox` for eBay's test site. |
| `pcgs_api_token` | PCGS certificate and price guide lookups. |
| `numista_api_key` | Numista catalogue estimates on world-coin deals, shown as estimates, never as sales. |
| `notify_service` | Leave it empty: the app finds your phone by itself when Home Assistant has exactly one, and its **Settings > Home Assistant** page lists every phone to pick from. Set it only to name a notify service yourself, such as `mobile_app_pixel_8`; a choice made in the app wins over it. |
| `publish_sensors` | Publish `sensor.coin_machine_*` entities for dashboards and automations. |
| `frame_ancestors` | Origins allowed to show the app inside a frame, such as `http://homeassistant.local:8123` for a dashboard webpage card. Empty blocks framing. |
| `public_url` | The address you open the app at, such as `http://homeassistant.local:3000`, used for links in phone alerts. Empty uses the address you last signed in from. |
| `timezone` | A time zone name such as `Europe/London`. Empty uses Home Assistant's time zone. |

Keys you leave empty here can be entered later in the app's **Settings** page instead. An option that is set always wins over a key saved in Settings.

The add-on log never shows your keys or a password you set: each appears only as "set". A password the app generated is shown there until you set your own.

## First sign-in

1. On a laptop on the same network as Home Assistant, choose **Open web UI** on the add-on's **Info** tab, or open `http://<home-assistant-address>:3000`, for example `http://homeassistant.local:3000` or `http://192.168.1.20:3000`.
2. Enter the access password. If you did not set one, copy the generated password from the **Log** tab.

To change the password later, set `access_password`, save, and restart the add-on.

## Use it on your phone

1. Connect the phone to your home Wi-Fi and open `http://<home-assistant-address>:3000` in Safari (iPhone) or Chrome (Android).
2. Sign in.
3. Add it to your home screen: in Safari, **Share > Add to Home Screen**; in Chrome, the menu then **Add to Home screen**.

Away from home, use Home Assistant's own remote access (for example a VPN such as the Tailscale add-on). Do not forward port 3000 on your router: the app is served over plain HTTP and is meant for your home network.

## Phone notifications

Install the Home Assistant Companion app on your phone and sign in to your Home Assistant. That is all: Coin Machine asks Home Assistant for its notify services, and when there is exactly one phone it sends BUY alerts there by itself. Tapping an alert opens the deal.

With several phones, or none, alerts go to Home Assistant's notification list until you choose. In the app, **Settings > Home Assistant** lists what Home Assistant has: pick one phone, all phones, or the notification list. Nothing is typed. The same page says where alerts go and why, and **Send a test notification** reports the service it called and Home Assistant's answer.

## Backups

The add-on keeps everything in its own data folder: the database, uploaded photos and the app's settings. Home Assistant backups include that folder, so a normal Home Assistant backup (**Settings > System > Backups**) saves your deals, positions, hunts and keys. The add-on stops for a few seconds while a backup runs so the database is copied in a consistent state, then starts again.

Restoring a Home Assistant backup that includes the add-on brings everything back.

## Troubleshooting

- **Install fails with "unauthorized" or "denied".** See the end of the Install section: the `ghcr.io` registry entry or its token is missing or expired.
- **The add-on stops right after starting.** Read the **Log** tab. A line starting with "Coin Machine cannot start" says which option to fix.
- **The page does not load on the phone.** Check the phone is on the home Wi-Fi, not mobile data, and that the address uses port 3000.
- **No phone notifications.** Open **Settings > Home Assistant** in the app: it shows the phones Home Assistant lists and where alerts go. **Send a test notification** names the service it called and Home Assistant's HTTP answer. Check also that hunts are running (the app's Hunts page shows the last run).
