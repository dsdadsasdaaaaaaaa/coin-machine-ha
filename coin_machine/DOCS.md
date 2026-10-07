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
6. Choose **Open web UI**, or turn on **Show in sidebar** and open **Coin Machine** from Home Assistant's sidebar. Home Assistant has already signed you in, so no password is asked.

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
| `ebay_environment` | `production` for real listings, `sandbox` for eBay's test site. A sandbox keyset (its App ID contains `-SBX-`) only works with `sandbox` and returns test listings, not real ones. |
| `pcgs_api_token` | PCGS certificate and price guide lookups. |
| `numista_api_key` | Numista catalogue estimates on world-coin deals, shown as estimates, never as sales. |
| `notify_service` | Leave it empty: the app finds your phone by itself when Home Assistant has exactly one, and its **Settings > Home Assistant** page lists every phone to pick from. Set it only to name a notify service yourself, such as `mobile_app_pixel_8`; a choice made in the app wins over it. |
| `publish_sensors` | Publish `sensor.coin_machine_*` entities for dashboards and automations. |
| `frame_ancestors` | Origins allowed to show the app inside a frame, such as `http://homeassistant.local:8123` for a dashboard webpage card. Empty blocks framing. |
| `public_url` | The address you open the app at, such as `http://homeassistant.local:3000`, used for links in phone alerts. Empty uses the address you last signed in from. |
| `accounts` | Off by default. Turn it on to give other people their own Coin Machine at one address, each with a username and a password. See **Accounts** below. |
| `share_keys` | Only with `accounts` on. Lets other accounts use the Anthropic, eBay, PCGS and Numista keys set here, at your cost. They are then shown no key settings and cannot change them. Off, each person enters their own keys in their Settings page. |
| `currency` | `USD` or `CAD`: the currency people here buy in. With `CAD`, every account can type a listing's price in Canadian dollars and sees Canadian dollars beside the figures to act on, at a daily reference rate. Coin Machine's own figures stay US dollars. Each account can change it for itself in Settings, Costs. Empty means US dollars. |
| `timezone` | A time zone name such as `Europe/London`. Empty uses Home Assistant's time zone. |

Keys you leave empty here can be entered later in the app's **Settings** page instead. An option that is set always wins over a key saved in Settings.

The add-on log never shows your keys or a password you set: each appears only as "set". A password the app generated is shown there until you set your own.

## Open it

**Inside Home Assistant** (the usual way): choose **Open web UI** on the add-on's **Info** tab, or turn on **Show in sidebar** there and open **Coin Machine** from the sidebar. It opens wherever Home Assistant does: on your home network, in the Home Assistant app on your phone, and away from home through your remote address (Home Assistant Cloud, for example). Home Assistant signs you in, so Coin Machine asks for no password of its own.

**By its own address**, on your home network only: `http://<home-assistant-address>:3000`, for example `http://192.168.1.20:3000`. This way asks for the access password: enter the one you set, or copy the generated one from the **Log** tab. To change it, set `access_password`, save, and restart the add-on.

Only administrators of your Home Assistant see Coin Machine in the sidebar and can open it this way. Everyone else needs its own address and the access password.

## eBay production keys

eBay hunts need a **Production** keyset, and eBay keeps a new one switched off until your application either
declares that it keeps no eBay data or subscribes to its "account deletion" notices. Coin Machine keeps each
seller's username and feedback numbers with a listing, so it subscribes, and it receives the notices itself:

1. Turn on **Accounts** and set **Public address** to an `https` address (see Accounts below). eBay only
   accepts a public https address.
2. In Coin Machine open **Settings, eBay, How to get eBay keys**. Step 3 shows a **Notification endpoint** and a
   **Verification token**.
3. On eBay's [Marketplace Account Deletion page](https://developer.ebay.com/marketplace-account-deletion)
   choose to subscribe, enter an email address for alerts, then those two values, and save. eBay checks the
   address at once. Then press **Send Test Notification**.
4. Copy the Production **App ID** and **Cert ID** into `ebay_client_id` and `ebay_client_secret` above, set
   `ebay_environment` to `production`, and restart.

From then on, when an eBay member closes their account, what Coin Machine holds of them (their listings, and
their name in a blocked-sellers list) is deleted, in every account.

## Kijiji and Facebook Marketplace

**Kijiji** needs nothing set up: on the Hunts screen add a hunt and choose **Kijiji** under **Where to search**, or add the starter hunt **Kijiji silver and gold**. Coin Machine reads Kijiji's public search pages and says who it is when it does. If Kijiji refuses a request, Kijiji hunts stop for six hours and say so.

**Facebook Marketplace** can be read two ways.

- **From your own browser, for every account.** On a computer, with Marketplace open, click the **Send to Coin Machine** bookmark on a search or category page (Analyze has the bookmark to drag to your bookmarks bar). Every listing on screen is sent; you keep the ones you want and they join the feed.
- **By itself, for the owner only.** The add-on carries a browser of its own. On the Hunts screen open **Facebook Marketplace**, press **Sign in to Facebook** and sign in yourself in the picture of that browser: click a field, type into the box under the picture, press Send. Then add a hunt with **Facebook Marketplace** under **Where to search**. Your password goes to that browser and is not kept by Coin Machine; **Sign out** removes the browser's profile from this server.

Facebook forbids automated reading, signed in or not, and restricts or disables accounts it catches doing it. Coin Machine's browser does not hide what it is, and the first time Facebook asks it to sign in again or to confirm who is there, every Marketplace hunt stops until you sign in again. The account you sign in with is at risk; that choice is yours.

A Marketplace listing found either way has a title, a price and a place, no photos. Open the one that scores well on Facebook and send it on its own for the full analysis.

## Accounts: one address for several people

Coin Machine holds one person's deals, settings and keys. Turn **Accounts** on and each person gets their own, behind one address and a sign-in.

1. On the **Configuration** tab turn on **Accounts**. Set **Public address** to the address people will open, for example `https://coins.example.com` (see the next section for how to get one). Save, then restart the add-on.
2. Open that address, or `http://<home-assistant-address>:3000` at home, and choose **Sign in**. You are `owner`; your password is the access password: the **Access password** option on the Configuration tab, or, if you left that empty, the one shown in the **Log** tab each time the add-on starts. The sign-in page names only the first of these, under **I run this Coin Machine**: anyone can open that page. Your own account page (`/account`) says both once you are signed in.
3. In the app go to **Settings > Access** and open the **accounts page** (`/accounts` at your address). Add a username. The page then gives you a message for that person: where to sign in, their username and password, where to set a password of their own, and how to get the iPhone app. Choose **Email it** or **Text it**, or copy the message. The password is shown that one time. If it is lost, open **New password** on that person's row, confirm, and send the new message: their old password stops working and they are signed out on every device.
4. For the iPhone app, send a second invitation yourself. The message asks the person to reply with the email address of their Apple ID. In [App Store Connect](https://appstoreconnect.apple.com/), add them under **Users and Access** with that address, then put them in a testing group on the app's **TestFlight** tab. Apple emails them the invitation; `/app` at your address walks them through the rest.

What to know:

- **Each account is separate.** Its own listings, hunts, settings, inventory and keys. Nobody sees anyone else's, including you.
- **A person's Coin Machine opens when they sign in** and closes after 30 minutes without use, so their hunts run while they are using it. Yours runs all the time, as before.
- **Memory.** Each open one uses about 300 MB. Up to six are open at the same time; a seventh person is asked to wait a minute.
- **Keys.** Other accounts enter their own Anthropic and eBay keys in their Settings page. With **Share my keys with other accounts** on they use yours, and what they spend is billed to you. Their Settings page then has no AI, eBay or PCGS section, nothing tells them to add a key, and they cannot change the keys or raise what the AI may spend: each account's automatic analysis stays at the built-in daily budget, and analyses they start themselves are not limited.
- **Yours only:** phone alerts, Home Assistant sensors and the options on this add-on's Configuration tab.
- **Inside Home Assistant** the sidebar entry now shows a link to the public address instead of the app itself: everyone, you included, signs in at the one address.
- **Passwords.** A person changes their own on their account page (`/account`; the message links to it). You can give them a new one, disable an account, or delete it with its data, on the accounts page. Your own password stays the `access_password` option.
- **The address in the message.** With **Public address** set, the message carries it. Without it, the message carries the address you are using when you add the account, and the page says so: an address on your home network opens for nobody outside it, so change it in the message before you send it.
- **On a phone.** `/app` at your address is a public page for the people you invite: how to get the iPhone app, which is in testing and comes by a separate invitation from Apple through TestFlight (step 4 above: you send it), and how to use Coin Machine in a browser or from a home-screen icon instead. An account here does not bring the app; the message links to that page.

To go back, turn **Accounts** off and restart. Your own data is untouched either way; other accounts' data stays on disk until you delete the accounts.

### A public address on your own domain (Cloudflare, free)

This puts the add-on at an address like `https://coins.example.com` without opening a port on your router. You need a domain whose DNS is at Cloudflare (a domain bought from Cloudflare already is).

1. [Open the add-on store](https://my.home-assistant.io/redirect/supervisor_store/), then the menu > **Repositories**, and add `https://github.com/homeassistant-apps/repository`. Install **Cloudflared** from it.
2. On Cloudflared's **Configuration** tab, leave **External Home Assistant Hostname** empty. Under **Additional Hosts** choose **Add** and enter:

   - hostname: `coins.example.com` (your own domain or a subdomain of it)
   - service: `http://53ba94f3-coin-machine:3000`

   Choose **Add**, then **Save**.
3. Start Cloudflared and open its **Log** tab. It prints a Cloudflare link: open it, sign in to Cloudflare, pick your domain and authorize. The add-on then creates the tunnel and the DNS record by itself.
4. Open `https://coins.example.com`. You should see Coin Machine's home page.

`53ba94f3-coin-machine` is this add-on's name inside Home Assistant. If the page shows a Cloudflare error 502, use your Home Assistant's own address instead, for example `http://192.168.1.20:3000`.

Turn **Accounts** on before you do this. With it off, the public address would lead straight to your own Coin Machine's password page.

## Use it on your phone

- **With the Home Assistant app**: open **Coin Machine** from the sidebar. It works at home and away, with nothing more to set up.
- **As its own home-screen icon**, on your home Wi-Fi: open `http://<home-assistant-address>:3000` in Safari (iPhone) or Chrome (Android), sign in with the access password, then **Share > Add to Home Screen** (Safari) or the menu then **Add to Home screen** (Chrome).

Do not forward port 3000 on your router: that address is served over plain HTTP and is meant for your home network. Away from home, open it inside Home Assistant.

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
- **A public address shows a Cloudflare error.** 1033 means the Cloudflared add-on is not running or not signed in: read its **Log** tab. 502 means it cannot reach Coin Machine: check this add-on is started and the `service` line is right.
- **"Too many Coin Machines are open right now."** Six accounts are in use at once. It clears when one has been unused for a couple of minutes.
- **No phone notifications.** Open **Settings > Home Assistant** in the app: it shows the phones Home Assistant lists and where alerts go. **Send a test notification** names the service it called and Home Assistant's HTTP answer. Check also that hunts are running (the app's Hunts page shows the last run).
