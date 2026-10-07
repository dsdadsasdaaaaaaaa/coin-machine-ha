# Changelog

## 0.8.0

More places to find deals, where Canadians sell: Kijiji and Facebook Marketplace.

- **Kijiji hunts.** A hunt can now search Kijiji: choose **Kijiji** under **Where to search**, or add the new starter hunt **Kijiji silver and gold**. Each keyword reads the newest page of ads across Canada, keeps the ones with a stated price, converts the price from Canadian dollars at the day's rate (the deal page keeps what the ad said) and scores them like any other listing. Ads that say "please contact", wanted ads and paid dealer ads are left out. Before an AI analysis the whole ad is read, with all of its photos. Kijiji needs no keys.
- **How it reads Kijiji.** Kijiji offers buyers no data feed, so Coin Machine reads its public search pages and says who it is when it does. It reads one page at a time with a pause between them, and if Kijiji refuses a request, Kijiji hunts stop for six hours and say so; nothing is done to get around a refusal. Reading the site this way is not something Kijiji's terms invite. It is the choice of whoever runs this Coin Machine.
- **A page of Facebook Marketplace results, in one click.** On a computer, with Marketplace open and signed in as yourself, clicking the **Send to Coin Machine** bookmark on a search or category page now sends every listing on screen: title, price and place. Coin Machine lists them, you untick what you do not want, and the rest join the feed, scored. A results page shows no photos and no description, so open the one that scores well and send it on its own for the full analysis. **Drag the bookmark to your bookmarks bar again to get this** (Analyze, "Send a listing in one click"). This way works for every account and asks nothing of Facebook: it reads what your own browser already shows you.
- **Facebook Marketplace hunts, for the owner.** The add-on now carries a browser of its own. On the Hunts screen, open **Facebook Marketplace**, press **Sign in to Facebook** and sign in there yourself: you see that browser's page, click in it, and type through the box under it. Your password goes to that browser and is not kept by Coin Machine. Then add a hunt and choose **Facebook Marketplace** under **Where to search**. Each keyword opens one Marketplace search, newest first, twenty seconds apart and at most every half hour, and the listings join the feed with a title, a price and a place, scored by rules. Open one on Facebook and send it on its own for the photos and the full analysis.
- **What you should know before you use it.** Facebook forbids reading it this way, signed in or not, and it restricts or disables accounts it catches doing so. Coin Machine's browser does not hide that it is automated. The first time Facebook asks it to sign in again or to confirm who is there, every Marketplace hunt stops and the Hunts screen says so; nothing is done to get around that. Use it knowing the account you sign in with is at risk. Other accounts on your Coin Machine are not offered it.
- The image is larger by the size of the browser, a few hundred megabytes.
- Kijiji has been read from this code against live pages, but no hunt has yet run inside a published Coin Machine. The Marketplace results page has been tested against the layout of its cards, not against Facebook itself. The Marketplace hunt has started its browser and met Facebook's sign-in page; it has never run signed in. The first hunt run, the first click and the first sign-in are the real checks.
- Kijiji and Facebook sales are private, in person and unprotected: check the coins before paying.

## 0.7.1

- The same as 0.7.0, which was never published: its image was stopped by the release checks because it carried the app's source files. This one does not.

## 0.7.0

- **Coin Machine can now receive eBay's account-deletion notices, which is what eBay asks for before it switches on production keys.** eBay keeps a new Production keyset off until your application either declares that it keeps no eBay data or subscribes to these notices. Coin Machine keeps each seller's username and feedback numbers with a listing, so it subscribes. With Accounts on and an `https` Public address, **Settings, eBay, How to get eBay keys**, step 3, now shows the **Notification endpoint** and **Verification token** to type at eBay. When an eBay member closes their account, what is held of them (their listings, and their name in a blocked-sellers list) is deleted, in every account. The documentation has the steps under "eBay production keys".
- This has not yet been exercised against eBay itself: **Send Test Notification** on eBay's page is the first real check.
- A sandbox keyset only ever returns eBay's test listings; the documentation now says so.

## 0.6.0

For people who buy in Canada. Coin Machine still works in US dollars (spot, melt and most listings are priced in them), and now meets Canadian dollars at the edges.

- **A new option, Currency people here buy in** (Configuration tab, under the optional options): `USD` or `CAD`. With `CAD`, every account starts in Canadian dollars. Each account can also choose for itself in **Settings, Costs**.
- **Type a price in Canadian dollars.** On Analyze, Lot X-ray and Capture a **C$ / US$** switch sits under the asking price. A Canadian price and its shipping are converted at the day's rate before anything is scored, and the deal page keeps what the listing said ("C$285.00 as listed"). A price the AI reads from a screenshot, or that comes with a shared page, is Canadian when the page marks it (C$, CA$, CAD).
- **Canadian dollars beside the figures you act on.** The deal page shows the asking price, the all-in cost and the max price in Canadian dollars beside the US figures; the Melt page does the same for spot and for the tally's offer, walk-away number and melt. The top bar shows the rate.
- **The rate** is a daily reference rate, not a bank's. If it cannot be read, the last one is used; with none ever read, Canadian figures are simply not shown and a Canadian price is refused rather than guessed.
- **Interac e-Transfer** is now a payment method, treated like Zelle: no way back if the coin never ships.
- **Kijiji** is named in the marketplace list.
- What you paid and what you sold for are still entered in US dollars, and eBay hunts still search eBay.com only. `docs/CANADA.md` in the repository lists what is left.
- The public pages now say their figures are US dollars.

## 0.5.4

- **The public pages say Coin Machine is private.** Where the home page, the tour and the sign-in page said "Accounts are by invitation", they now say it plainly: private for now, the person who runs this Coin Machine makes each account themselves and only for people they have agreed it with directly, and there is no sign-up, no waiting list and no public price. The tour's question about getting in is now "How do I get an account?" and gives that answer.
- The smallest text on the home page is now 12 px, as on the tour.

## 0.5.3

- **The tour starts with the short version.** A tester found the tour confusing and asked for it to be simpler at the start, with more for those who want it. It now opens with what Coin Machine is in two sentences and one example followed through: someone is selling 40 silver quarters for $285, what they are worth and what could go wrong, and the answer (Buy, and the most to pay). A visitor can stop there. Everything the tour had is still there behind nine cards that open, in two optional parts: "A closer look" and "How it decides". Each opened part starts in plain words, and the app's own figures and reasons are one tap further.
- The home page says the same thing in plainer words.
- Every picture of the app on the home page and the tour was retaken from this version.
- Fixed: on a tablet held upright, the third of the three phone pictures on the home page was cut off.
- The AI's reading of listings works on the live Reddit hunt since 0.5.2. What it says is now worded the same everywhere: "AI estimate", and "the AI" in the messages you see when a reading fails, where some places still said "the model".

## 0.5.2

- **The AI's reading of a listing was still refused.** 0.5.1 fixed the limit Anthropic named, and the next live run met a second one that cannot be measured ahead of time ("The compiled grammar is too large"). Coin Machine no longer depends on it: the format of the AI's answer for a listing is now given to the AI as written instructions and checked by Coin Machine when the answer arrives, instead of being enforced by Anthropic's servers. If any other format is ever refused the same way, Coin Machine switches that one over by itself and carries on.

## 0.5.1

- **Fixed: the AI's reading of a listing was refused every time.** The first live runs showed Anthropic turning the analysis request away before reading it ("too many parameters with union types"): the answer format had 19 fields that could be left empty, and the API allows 16. Listings were still saved and scored by the rules, but none got the AI's reading of its photos. The format now has 3, a test counts every format Coin Machine sends, and nothing that is stored or shown has changed. A listing saved in the meantime can be read by the AI from **Run AI analysis** on its deal page.

## 0.5.0

Easier to use, everywhere. Nothing was removed; what you came for is now first, and the rest opens when you ask for it.

- **Every page starts with what it is for.** On a phone the first listing, the verdict, the first field or the first hunt is on the first screen. Tiles of figures became one line with **All figures**, notices became one line with **More**, and each page has one gold button: the next thing to do.
- **A deal page is three screens, not twelve.** The verdict, the action, the max price, the expected profit and the reasons come first. The math, what can go wrong, fair value, sold comps, the AI report and the rest are sections that open, each showing its key figure while closed ("All-in $285, nets $403"). A section with a warning in it opens by itself. Once you scroll, the verdict and **Add to pipeline** stay at the top.
- **Settings is a list.** Each section shows what it is set to ("Flip for profit, up to $5,000 a deal") and opens on a tap. A link to a section opens it.
- **A "?" beside the words a newcomer will not know** (max price, all-in cost, fair value, score, low case, confidence, melt, sold comps, AI estimate only, walk-away number): tap it for one to three plain sentences. One wording for the whole app.
- **Bigger things to press on a phone.** Every button, tab, switch, menu and field is at least 44 px on a touch screen, nothing is set under 12 px, a row shows its one main action by name with the rest in a "..." menu of named actions, and nothing explains itself only when a mouse hovers over it.
- **One name per thing.** Max price (not max buy price), Scored for (not goal or profile), listing, hunt, verdict, sold comps. The downloaded spreadsheets use the same names.
- **Analyze**: the photo button and the fields come first; single listing or lot is chosen after. **Hunts**: a new hunt asks for what matters and keeps the rest under More options. **Advisor**: example questions sit above the box and fill it when tapped. **Melt**: the tally comes first, and its walk-away number explains itself.
- **Handing someone their account.** Adding an account now shows one message to send, with **Email it** and **Text it**, and says plainly that the iPhone invitation is a second step you send from App Store Connect, for which you need the email address of their Apple ID (the message asks for it). If no public address is set, the page warns that the address in the message only works on your network. **New password** asks before it acts.
- **A page about the iPhone app** at `/app`, open to anyone: how to install it through TestFlight, what it adds, and that any browser works until then. The message to a new person links to it.
- **Someone on your keys reads plain words.** When eBay or the AI refuses a request, another account is told what happened and to let you know, not about keys, calls or quotas. Your own messages keep their detail.
- The iPhone app can print: the show kit and the melt table open the phone's print sheet. This needs the next build of the app from TestFlight.
- Fixed: the "Add item" form could scroll sideways on a phone; a dialog's close button sat on its first line of text.

## 0.4.1

- **What another account is told about its data is now true for it.** Someone signed in to your Coin Machine from their own phone was told their listings were "stored on this computer", shown this server's folders and free disk space, and given commands only you can run. An account other than yours now reads that its data is kept in its own Coin Machine, apart from every other account's, sees no file paths, and is told that restoring a backup is done on the server by its owner. Its own backups, downloads and diagnostics are still there. Your own pages are unchanged.
- A few messages that spoke of "this computer" when they meant the server now say only what the reader can act on.

## 0.4.0

- **An introduction.** The first time someone opens Coin Machine, after the "Before you start" notice, a one-minute introduction sets it up for them: the kind of buyer they are, their numbers, how to read a verdict on a listing from their own feed, and how to bring a listing in. It can be skipped, and taken again at any time: **Introduction** in the navigation, the button at the top of Settings, or Settings > Help. Taking it again changes nothing unless you change it.
- **Navigation on a phone.** A bar along the bottom with the Deal feed, Hunts, Pipeline, Melt and **More**, which lists everything else. It replaces the menu button at the top left, and nothing has moved out of reach.
- **Accounts on your keys see no key settings.** With **Share my keys with other accounts** on, another account's Settings has no AI, eBay or PCGS section, nothing tells them to add a key, and they cannot change the keys or raise what the AI may spend. Their goal, numbers and data stay their own. Without that option nothing changes: each person adds their own keys.
- **Ready for the iPhone app.** The pages know when they are shown inside the app: there, **Share, then Coin Machine** takes the place of the bookmarklet, and photos and screenshots shared from the phone arrive on the Capture page ready to analyze. The app itself is installed through TestFlight, not through this add-on.
- Fixed: on a phone, opening a page at one of its sections could push the top bar off the screen with no way to bring it back.

## 0.3.3

- The home page and the tour no longer carry a "Where it stands" list. The tour is nine stops.
- The public pages no longer say that a visitor needs keys of their own: accounts here are by invitation and come ready to use.
- With accounts on, your address now tells iPhones that links to it belong to the Coin Machine app, so a link can open there once the app is installed.

## 0.3.2

- **The tour says what to do at every stop.** Each stop that can be used now has one line that says how ("Swipe sideways, or tap Next", "Tap a buyer to rescore the listing", "Drag the slider, or tap − and +"), and that line changes once you have done it. Everything that can be pressed now looks like a button, every stop ends with a link to the next one, and the first board sorts itself.
- On the tour, a sideways swipe that began on one of the phone screens did nothing, so the row of screens could only be moved from its edges. It now moves from anywhere, and the Previous and Next buttons sit above the row with a count.
- The tour's progress bar is part of the top bar, so the page no longer shows through it, and on a wide screen each segment carries its stop's name.
- The tour no longer scrolls sideways on a small phone, and its list of stops no longer overlaps itself in Safari on iPhone.

## 0.3.1

- With accounts on and an `https` public address, a request that arrives for that address over plain `http` is now sent to `https` before anything else, so a password or a session can never travel unencrypted. Browsers that have visited are told to keep using `https`. Your home network address is unaffected.

## 0.3.0

- **Accounts.** Turn on the new **Accounts** option and Coin Machine has one address where everyone signs in with a username and a password. Each account is its own Coin Machine, with its own listings, hunts, settings, inventory and keys. You are `owner` with your access password, and you add, switch off and delete accounts on an accounts page. Off by default: nothing changes until you turn it on.
- **A home page and a tour.** With accounts on, a visitor who is not signed in sees a home page and an interactive tour, with a Sign in button.
- **A public address.** The documentation has the steps for putting the add-on on your own domain through Cloudflare, with no port opened on your router.
- New option **Share my keys with other accounts**, off by default: other accounts enter their own AI and eBay keys unless you turn it on.
- With accounts on, the sidebar entry inside Home Assistant shows a link to that one address instead of the app.

## 0.2.1

- Steadier inside Home Assistant. On port 3000, an address without the add-on's own path (an old bookmark, a typed address, the link in a phone alert) is now sent on to the full address. Before, the add-on fetched it a second time from itself, which failed now and then: a photo could come back as an error.
- The health check that Home Assistant's Watchdog uses no longer goes through that second fetch.

## 0.2.0

- Coin Machine now opens inside Home Assistant: use **Open web UI**, or turn on **Show in sidebar** and pick it from the sidebar. It works wherever Home Assistant does, including the phone app and your remote address (Home Assistant Cloud), and asks for no password there because Home Assistant has already signed you in.
- **Open web UI** no longer hangs when Home Assistant is opened through a remote address. It used to point at port 3000, which a remote address does not carry.
- The address on your home network (`http://<home-assistant-address>:3000`) still works and still asks for the access password.

## 0.1.3

- Silver sold by face value is read from the shorthand sellers use, with no "silver" in it: "$5 FV 90% quarters", "$10 face 90%", "$2 FV 40% halves".
- Lines under a coin heading that follows another metal's section ("Morgans" after "GOLD") are read as that coin, not as the earlier metal, and a line that is only a date under such a heading is no longer dropped.

## 0.1.2

- One switch for who is buying: "Scored for" in the feed header rescores every listing for a flipper, a stacker or a collector. The feed and the deal page then show that buyer's figure (profit, saving against a dealer, or saving against fair value).
- A stacker's Buy is now a real saving: it has to survive the odds of a fake and of a parcel that never arrives, so a private sale paid by Zelle needs a wider margin than a dealer listing, and the deal page shows the arithmetic. Coins that dealers sell far over melt (a silver Libertad) are no longer called a stacker's buy.
- Buyer protection is no longer assumed: a post that says "no G&S" or adds a fee for it is treated as a sale with no protection.
- Reddit listings no longer pile up: a line that sells or is edited out ends at the next run, a post that leaves the feed ends after a day, and ended ones are removed after a week.
- A repost or a cross-post is one listing with a price history, not three copies.
- The Reddit hunt now brings in every priced item up to $6,000 instead of only lines that name a metal. An unedited hunt from 0.1.1 is widened on its own; one you changed is left alone.
- More lines are understood: dates listed under a heading ("1984" under "Libertads"), fractional sizes ("1/10th oz"), stated silver weights ("0.67 oz ASW"), Canadian silver, commemorative halves and dollars, Mexican crowns and onzas, lots priced as a whole.
- A photo album linked beside one item is opened from that item's page.
- A probable fake no longer shows "max $1": it shows no max price and says why.
- Run hunts works without eBay keys (it runs the hunts that need none), and the Hunts page no longer says the Reddit hunt is waiting for them.
- Deal pages scored at an offer now say so beside each figure instead of quoting the return on the asking price.
- Scores are recalculated once after this update.

## 0.1.1

- Real listings with no keys: a Reddit hunt (r/Pmsforsale and r/CoinSales) is added on the first start and runs every 30 minutes.
- Phone alerts need no set-up: the app finds your phone in Home Assistant by itself, and Settings > Home Assistant lets you pick one phone, all phones or the notification list, with a test button that reports what was sent.
- Reddit price lists are read far more carefully: postage, spot quotes and "take all" prices are no longer listed as items, a coin's denomination is no longer taken for its price, and each line keeps the metal and size of the heading it sits under.
- A line whose price does not fit what it reads as is left unvalued with a note instead of being called a fake.
- Max price: a seller asking near melt no longer drags the max price down to a few dollars, and a small item now says "too small to clear your minimum profit" instead of an unrealistic price.
- Inventory: an estimate you type for an item now stays, instead of being replaced by the linked listing's live value. Clear it to follow the live value again.
- Phones: the first-run notice, the hunts page, auction deals, the show kit and Settings no longer run off a narrow or short screen.
- Pasting a listing without an AI key no longer reads "$10 face" or "$20 Saint-Gaudens" as the price.
- The generated sign-in password is shown in the Log tab on every start until you set your own.
- Every image is now started and tested the way Home Assistant runs it before it is published.

## 0.1.0

- First Home Assistant add-on release.
- Runs on 64-bit Home Assistant systems (amd64 and aarch64) on port 3000.
- Password sign-in for the laptop and phone.
- Hunts run on a server-side schedule; new BUY deals can be sent to a phone notify service.
- Options for the Anthropic, eBay and PCGS keys, phone notifications, sensors, framing and time zone.
- Data lives in the add-on's folder and is included in Home Assistant backups.
