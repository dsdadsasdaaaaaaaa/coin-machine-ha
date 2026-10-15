# Changelog

## 0.21.1

- **Gold sold for cash at half its gold is treated as the likely fake it is.** A 1 oz American Gold Eagle asked $3,150 for cash in Leamington, with about $5,900 of gold in it, was given 4% odds of a fake, called "priced well" and marked "Below dealer bid" in green. Gold, platinum and palladium bullion (named coins, bars and rounds) no longer get the allowance a local cash sale gets for old coins, whose heirs do sell them cheap. The same ad now has 44% odds of a fake, and the advice is to test its weight and diameter in hand before offering up to $2,935. Silver bullion, old coins and world gold keep the local allowance.
- **"Worth" says "if genuine" when a fake is likely.** The card and the deal page say "If genuine, the gold alone is worth $5,929". The room under that figure is no longer drawn in green, and a price that low is no longer called "Below dealer bid". An offer that waits on a check says so ("check it, then offer up to $2,935") instead of "A buy at $2,935 or less".
- Every listing is scored again after the update.
- For the people working on it: the unit tests now pass on Windows (the 37 that need Linux file permissions or paths are skipped there and still run before every image), and selling from My coins has a browser test.

## 0.21.0

**Everything from the audit of 15 October that was not the owner's to do.** (`docs/AUDIT.md`, items 1 to 136; what was left out is at the end.) After this update **everyone signs in once more** and is asked to accept the terms again.

**The first ten minutes**
- **New today.** The top of Deals lists every ad put up in the last day, whatever its verdict, one line each with its photo, so a lot the rules cannot value is still seen by someone who can.
- **The app is right before it finds a Buy.** With nothing worth a look, Deals shows the passed listings that came closest, each with its verdict in a sentence, instead of an empty box.
- **Nothing you turned down is in your feed.** No search runs before the questions are answered (the US Reddit starter is gone), and a search you switched off takes its listings with it. What you saved stays.
- **A coin you type into Check is in hand** unless you say it is shipped: no shipping, no odds it never arrives. One tap switches it. A 1967 silver dollar at $40 against $48 of silver was a Pass with a max of $24; it now says what it is.
- **The introduction's defaults fit a Kijiji buyer**: all six kinds of coin and all three ways of selling ticked, $500 for one deal, and "Skip for now" keeps Canadian dollars.

**Seeing more, sooner**
- **Every new ad is read whole as it arrives** (up to 12 a look, and older ads a few at a time), so the rules, the AI and you see the same text and photos. The broad newest-first search runs every 10 minutes, your own words every 30. Kijiji is asked about twice as often as before, roughly ten pages an hour for a city.
- **Searches for people who do not know what they have**: old coins, coin collection, estate coins, foreign coins, lot of coins, inherited coins, and in French where French is spoken. "Anything underpriced" uses these lot words, not the bare word "coins" that brought vases.
- **Facebook Marketplace joins your searches by itself** once the server is signed in to Facebook, without asking the questions again. Sold and pending ads are skipped, a Marketplace listing not seen for five days is presumed gone, and every read is logged.
- **The Looking-for card says the yield**: "Checked 12m ago · This week: 35 seen, 1 worth a look". "Look now" on Deals runs your searches; the Run hunts button is gone.

**Figures you act on**
- **A pass says the money**: "it loses $88 after selling", "under its silver, but only $1 in it after selling". A Watch priced well says what holds it back ("priced well at $50, but not sure enough of it for a Buy"), and one held only by your per-deal limit says "Over your $500 limit" instead of a max price nobody would pay.
- **Coins sold by weight** (a pound of dimes, 500 g of Canadian 80%) are valued as coins of their silver, not as fine silver. Small gold bars take a small bar's dealer price. A price "each" is no longer multiplied by the count.
- **Canadian costs**: Canada Post's price for a parcel (C$25.54 with fuel surcharge and HST), eBay.ca's fees with HST, and 13% HST on an eBay purchase from a Canadian seller. Sold prices marked C$ stay Canadian; an AI reading made in US dollars is converted once and labelled.
- **Canadian silver by date and grade**: 17 common-date tables for Victoria to George VI silver from certified sales, and five varieties (1935 short water lines and double XXV, 1951 Arnprior, 1899 large 9s dime, 1936 bar dime).
- **Reading Canadian ads**: "silver dollar" is Canada's where Canada struck one that year, a two-date anniversary title ("1774-1999") is read as its later year, a dealer's name such as Silver Gold Bull is not a second metal, and a coin weighing what a later issue weighs is no longer called a fake.
- **Offers that stall**: three days with no reply brings a nudge, seven passes the listing by itself. Bought it and Sold it are one short step each, filled in with the engine's fees and shipping.
- **Alerts about a listing under its metal value** only when there is money in it: a Watch with a profit of 10% or more, never a Pass.
- **The AI** rests after seven days unopened instead of one, never spends past its daily budget, costs about a fifth less to read a cold listing, and on someone else's server the paid check is the owner's to run.

**Simpler pages**
- **A deal** has its actions right under the price card, two parts instead of three (Why and The math), the money in two sentences ("Pay up to $62. You would make about $28, or $26 if it grades low"), and two "?" on a phone where there were ten. Confidence is no longer a meter: a Watch says when it is not sure enough for a Buy.
- **Pass means Passed**: what you pass goes to the Passed tab, where you can restore it. Save, Pass and Add to My coins are the only three words for those actions.
- **Deals on a phone**: filters in a sheet, a short note on what the tabs mean, counts that stay put. **Check** leads with the title and price when there is no AI, and its button says "Check it". **My coins** has one gold button, the next step, and one step per row. **Settings**' Advanced is eight parts, the dealer rates moved there, and **Change** on the Looking-for card opens the questions over the page you are on.
- **Gone**: the Guide, Sets, Want list, Advisor and Show kit pages, and the code behind them. Their addresses open Deals. Two money errors went with them, and a third was fixed on the way: Metal values' key-date values were US dollars under a Canadian "$".

**The server**
- **Restore a backup from Settings, Data, or from the accounts page**, even when a copy cannot start. A copy that cannot start says why, the owner's page offers Try again, and five crashes no longer stop the whole add-on.
- **Sign-in is limited**: five wrong passwords a minute from one address, and a username tried too often from anywhere is held for a minute, doubling to 15. A device that signed in before is not held. A changed password ends every session.
- **eBay's account-deletion notices are acted on only when eBay's signature checks.** Set the eBay keys before registering the endpoint, or eBay's test notice is refused.
- **Testers see no server paths**, usernames cannot take the names of the server's own files, uploads are capped at 16 MB, and a backup that failed or stopped is shown in amber.
- **Releases are tested first**: the image is built only after the unit tests pass on Linux. It is built for Intel and AMD machines (amd64) only, which is what this server is; a Raspberry Pi image is no longer made.

**Terms**: they now name Kijiji, Reddit's sale boards and (once the owner signs in) Facebook Marketplace as read from public pages, say an account can live on someone else's server, what is kept about you and who deletes an account. `docs/LEGAL.md` lists what is still for the owner and a lawyer.

**iPhone app (needs the next build)**: it asks once whether to send alerts, links open in their own apps, signing out lets go of the alerts, the badge counts what you have not seen, and it is an iPhone app (no iPad layout). The server already checks each phone's alert set-up with Apple and says when it is wrong.

**Not done**: modern MS69 and MS70 bullion by year (the sales sites refused automated reads, and that stands); the Chromium reader still runs as root, with a cleaner environment only; a failing backup does not yet send an alert; GST and HST at the border on US purchases are still an estimate; proof and double-dollar sets, $20-for-$20 and worn Victorian silver have no sales table; the public site still shows 11 October's US samples (next release). The owner's: the Apple push key, eBay production keys, a Marketplace sign-in, the TestFlight build, and one purchase taken from offer to sale.

Not seen running: eBay's signed notices, a restore on the server, the first tested image build on Linux, Marketplace on the server, any AI change (no AI call was made), the iPhone app changes. The reading and the pages were seen on 64 real Toronto Kijiji ads on a fresh copy.

## 0.20.0

- **It knows Canada's key dates.** 52 Canadian coins that are worth far more than their metal are recognised by date and variety: the 1948, 1947 Maple Leaf, 1945 and other silver dollars, the 1921, 1890H, 1932 and 1948 50 cents, the 1875H and 1936 Dot 25 cents, the 1889 and 1893 Round Top 10 cents, the 1921 silver and the 1925 and 1926 Far 6 nickel 5 cents, the 1923 and 1925 cents, and more. Each is valued from what examples actually sold for at Canadian and US auctions in 2022 to 2026, and the deal page names those sales. A 1948 dollar on Kijiji used to be worth its silver to the app; now it is worth a 1948 dollar, and an uncertified one is held for checking (weight, size, the date under a glass) before it can be called a buy.
- **Fakes and impossible coins.** A raw 1921 50 cents ("King of Canadian coins") is flagged as an altered date or a copy, as is any 1936 dot cent or 10 cents (three and five exist). A "1947 Maple Leaf" dollar is no longer read as a one-ounce silver Maple Leaf.
- **Canada's grading services.** ICCS and CCCS are named as what they are instead of "third-tier holder", and a Canadian coin in one is valued at the grade on its certificate.
- **Buying from home.** A coin sold from Canada to a buyer in Canada is no longer warned about as shipping "from outside the US".
- **Fixed:** a card could say "Not valued yet" and "It is worth about $45" at once. It now says there is not enough to say what it is worth.
- **For the iPhone app:** alerts about one listing carry its photo, with Open and Pass under them, and there is a home-screen widget with the best find and gold and silver. The server now sends what they need; they arrive with the app's next build (2.2), once it is through TestFlight.

## 0.19.0

- **A map of what is near you.** Deals has a Map button beside Worth a look, Saved and Passed. It draws your city in the middle with rings at 10, 25 and 50 km, and a pin for every listing that says where it is: green for a Buy, gold for one priced under its metal value, amber for a Watch, grey for a Pass. Press a pin for its card and Open; a pin with a number holds several listings in one place, and pressing it again moves to the next. Anything farther than 50 km sits on the edge with its distance written beside it. It is a drawing, not a street map: no map service is asked for anything and nothing about you leaves your Coin Machine.
- **Where the positions come from.** Kijiji ads carry one, and it is kept to about 100 m. A listing already stored gets its position the next time Kijiji shows it; listings from other sources are counted under the map as having none.
- **Kept out:** a toy sold as a "coin" (a Lego amulet reached the feed on a real search).

## 0.18.2

- **More accounts no longer means more asked of Kijiji.** With Accounts on, everyone's Coin Machine leaves from your one address, and since 0.18.0 they all keep searching. They now share what they read: a Kijiji page one account read in the last ten minutes is used by the others instead of being asked for again, the five-second gap is kept between all of their requests together, and if Kijiji refuses one, all of them pause. Only public pages and the times of requests are shared, nothing of anyone's account.

## 0.18.1

- **The public pages show the app as it is now.** Every picture on the home page and the tour was retaken from this version (eight phone screens and six on a computer), the pages that no longer exist are gone from them, and the figures in the tour's examples are the ones the app gives today. They now say where listings come from (Kijiji near you, eBay, and anything shared or pasted) and that an account in Canada keeps its figures in Canadian dollars.
- The **Want list** filter is gone from Deals, and Metal values no longer points to the Guide: both pages left the menu in 0.16.0.
- In the iPhone app (needs the new build): the background check announces a listing under its metal value as well as a Buy, in the same words the server uses.

## 0.18.0

**It tells you, it knows Canadian coins, and it keeps looking for everyone.** (`docs/AUDIT.md`, items 8, 9, 11 and 12.)

- **Alerts for more than Buy.** You are now told when a listing is priced at or under 92% of the value of its metal and is near you, even when it is not rated Buy: "Under its metal value: ...", with the asking price, the metal's value and the distance. At most three a look and eight a day, and never the same listing twice.
- **A line a day when nothing was found.** In the evening: "Checked N listings today. Nothing worth your time." Not sent on a day with an alert or with no new listings. One switch in Settings, Alerts turns it off.
- **Royal Canadian Mint coins are known.** The cased silver dollars by era (and the nickel dollars that hold no silver), the yearly proof and double dollar sets, the $15 Lunar coins and the one-ounce $20 are read for what they hold. Where a set holds more silver than can be said for certain, the figure is the silver dollar alone and is marked as a floor. Weights and purity only: no price is invented.
- **Other accounts keep searching while their people are away.** With Accounts on, each person's Coin Machine now starts with the server and keeps running, so their searches and alerts do not stop 30 minutes after they leave. Two new options: **Keep searching for everyone** (on) and **Accounts open at once** (6). Each running account uses about 300 MB of memory; turn the first off, or lower the second, on a small machine.
- **Alerts can reach other accounts' phones.** The app's push key is now given to every account's Coin Machine, not only the owner's.
- **The AI reads what the rules cannot.** Its automatic turns go first to sets, lots and collections the rules could not value, then to other unvalued listings with photos, then to rule Buys and close calls. Same model, same daily limit. A search's line says what it read.
- **"Silver" is also a colour.** A title now has to name a coin or bullion, or a metal with a weight, a fineness or a face value: a "Silver Sheen Obsidian" crystal ball was being read as 27 grams of silver. Things that are not coins and were let in by earlier versions are removed once after the update, unless you saved them.

Not seen running: the alerts on a phone, the AI's new choice (no AI ran in testing), and six accounts running at once on a real server.

## 0.17.0

**A phone app that looks like one, and half the pages.** (`docs/AUDIT.md`, items 14 to 17, 19, 20, 24 to 26, 29, 30 and 32.)

- **Deals on a phone.** Each listing is a card led by its photo, with the verdict on the photo, one large figure, and one sentence: what the seller wants, what it is worth, what to do. Two or three fit a screen where one did. The title shrinks as you scroll and the tabs stay under it.
- **The deal page starts with the photos**, full width, to swipe through. Under them: the verdict in a sentence, one bar showing the asking price against what it is worth and the most to pay, and the three main reasons. A bar along the bottom holds Save, Pass and the one thing to do next, which on a local ad is **Message seller** with the message already written.
- **Three parts instead of thirteen.** Why, Risks and The math each open as a sheet. What-if, "what this verdict hinges on", the offer ladder and the standing forms are gone from the page; "Something wrong?" in The math is where a misreading is corrected.
- **The phone's own look.** Inside the iPhone app and on a phone, text is set in the phone's own typeface, the main button is gold, cards have depth, pages move into each other, and actions give a tap you can feel.
- **My coins** is one page in place of Today, Pipeline, My coins and Your record: what to do next, what you hold, what you sold, with money out, value now and profit at the top. When nothing is rated Buy it shows the nearest things to a deal instead of an empty page.
- **Check** is one page in place of Check a listing and Value a lot: take a photo, add photos, or paste a link or the listing's words. Whether it is one item or a lot is worked out for you.
- **Set-up is four screens**, one question each, and the "analysis tool, not advice" note is shown once.
- **Settings for someone on another person's Coin Machine is four things:** what you are doing, the most for one deal, your city, and alerts.
- **Metal values** is the pile calculator, with Canadian pieces first.
- **In the iPhone app (needs the new build):** one page before sign-in instead of three, and the second tab is My coins.

## 0.16.0

**It reads real listings right.** A fresh set-up was run on 270 real Kijiji and Reddit listings and each one checked by hand; this release fixes what that found (`docs/AUDIT.md`, items 1 to 7, 10, 23, 26 to 28, 31 and 36).

- **Sets are valued as sets.** A 1976 Montreal Olympic four-coin set was valued on one coin's silver, which hid nine sets priced under their metal. Olympic and 1967 sets are now known, a stated total beats adding parts, and years in a title are no longer counted as coins. A set whose content is not known is left unvalued instead of guessed.
- **No more offers nobody would take.** A listing is not marked "worth a look" on an offer far under its asking price and below what a dealer pays for the metal. It is a Pass: "no offer worth making, a dealer would pay the seller more".
- **Kijiji results are coins.** Searches stay in the collectibles category, an ad must name a coin or bullion in its title, and jewellery, pens, tableware and toys are dropped. An ad first posted over six months ago is kept only if the seller bumped it this month, and "New" is for ads posted in the last two weeks.
- **The whole ad is read** for anything that looks good, without the AI. Before, every Kijiji ad was judged on its first 200 characters and one photo, and every one carried a false "Only one photo" warning.
- **New ads are seen sooner.** Every look reads the newest ads of one broad search as well as one of your own.
- **Canada from the first screen.** A new account keeps its books in Canadian dollars whether or not a city was picked. Picking up nearby needs your nearest city (or **Use my location**), so "local" no longer means six provinces.
- **Reddit is off unless you ask.** Its sellers are in the United States, price in US dollars and mostly do not ship here. One switch under "How do you want to buy?" turns it on. The built-in Reddit search stops once you have your own.
- **Small misreadings.** A banknote is not a silver dollar. A mint's gilded silver coin is silver, not "plated, walk away". "1/2 gram" is a weight. A graded collector coin with no table value says "not valued by the rules" instead of showing its metal as its worth. Lines of a Reddit post that are terms, not items, are no longer listings.
- **Fewer pages.** The menu is Deals, Check, Today, Pipeline, My coins, Your record, Metal values and Settings. Sets, Want list, Guide, Coin show sheet, Advisor, Value a lot and Hunts still open at their addresses.
- **Fewer words.** The paragraph of cautions on every deal is one line, and in the iPhone app the legal line is no longer under every page (it is in Settings, Help).
- **Sell this** leaves out the US Reddit board for a Canadian-dollar account, and says so when every asking price is under what you paid.
- **Fixed:** on a phone, opening Filters crushed the Worth a look, Saved and Passed tabs into each other. "Spot price is stale" no longer shows on a price fetched minutes ago.

Not seen running: the collectibles search address is taken from Kijiji's own pages and falls back to the old search for a day if Kijiji refuses it.

## 0.15.1

- **Find deals failed with "Your searches could not be made"** for anyone who had not picked a city (for example with "Shipped to me"). Saving "no city" was refused by the database. It is now saved as it should be. Found on the first live run.
- In the iPhone app, More lists every page the tab bar does not hold, whatever version the server is on (needs the new app build).

## 0.15.0

**From finding a deal to selling it on.**

- **Today.** A new page, and the second tab on a phone: what there is to do, in order. **Buy** lists what is rated Buy, **Waiting on a reply** holds the offers you sent (with a nudge after a day), and **Ready to sell** holds what you bought. Each row ends in one press: Offer sent, Bought it, No deal, Sold it. It is the Pipeline board as a to-do list; the board is still there.
- **Sell this.** On anything you bought, one button gives you the ad: a title and description, what to ask at each place you sell, the photos from the listing you bought it from to save and reuse, and buttons that open eBay's, Kijiji's or Marketplace's own page for a new listing. You paste and post it yourself: nothing is posted for you.
- **What has earned.** Today shows your realised profit by where each item was found, and the weekly tuning of your searches now follows what actually made money.
- **Verdicts in a sentence.** On a phone each listing says what the seller wants, what the thing is worth and what to do: "Seller wants $320. The silver alone is worth $387. Buy it."
- **Meet-up mode.** On a listing you buy in person, **I'm at the meet-up** opens four checks with big buttons (magnet, weight, width, does it match the photos), shows the most to pay, and records the purchase in one press.
- **Price drops and metal moves.** A listing that turns into a Buy after you first saw it (the seller dropped the price, or silver moved) is now announced like a new one.
- **Sellers who may take less.** "Must sell", "OBO", "moving" and the like are noticed, and the opening offer written for you goes further under the asking price.
- **Kijiji is looked at every half hour.** Two of your searches at a time, in turn, so new ads are seen sooner without asking Kijiji for more pages in a day.
- **One card per item.** The same ad posted on Kijiji and on Marketplace is shown once.
- **A $10 with maple leaves on it is half an ounce.** The Mint's $10 "Maple Leaves" coins were being read as the 1 oz Silver Maple Leaf, which doubled their silver. Found on a real Kijiji ad.
- **In the iPhone app (needs the new build):** the tabs are Deals, Today, Check and More.

Not built: more Canadian sources. MaxSold answers a plainly labelled request with a browser check, and Coin Machine does not work around those. eBay's own API for posting a listing for you is also not built: it needs you to grant eBay selling access, and is a project of its own.

Checked on a test copy and by tests. Not yet used on a real purchase from offer to sale.

## 0.14.0

**The numbers are worked out for how you actually buy and sell, in Canada.**

- **How do you sell?** The questions now ask: locally for cash (Kijiji, Marketplace, in person), on eBay, or to a dealer. A listing's profit is worked out for the way you sell. Selling locally for cash is new: no fees and no shipping, at a little under what eBay brings. Before this, profit was always worked out as if you sold on eBay or a US forum.
- **What your dealer pays.** Settings has two optional boxes: the share of the metal's value your dealer pays for silver and for gold. Anything listed under that can be sold the same day for more, and it becomes the floor every listing is checked against. Left empty, typical dealer prices are used.
- **Canada is home.** For an account in Canadian dollars, a listing in the United States is now the one that crosses a border, with import charges and a longer wait, and a Canadian one is not. eBay searches ask only for what ships to Canada and price the shipping to your city.
- **Eight more Canadian coins** the app can recognise and weigh: the silver five cents, the 1967 gold $20, the Mint's $20 for $20, $50 for $50 and $100 for $100, the $10 half-ounce commemoratives, and the 1988 Calgary Olympic $20. Their weights were entered from the Mint's published figures as remembered, not re-read from the Mint's pages: weigh one before trusting it.
- **Fewer wrong "worth a look" listings.** The rules were run against real Kijiji ads and corrected where they were wrong: a lapel pin, a signed hockey puck and a pearl bracelet are no longer read as silver coins; an ad whose title says SOLD is passed; a seller who says the price is firm is not shown as open to an offer; a listing that would only work at a price far under its asking price is a Pass instead of a Watch; and "(9x) ... $320 each" is priced as one, not nine. On the test copy this took 15 listings rated worth a look down to the ones that deserved it.

Checked on a test copy against about 300 real Kijiji ads. Not checked: eBay searches from Canada (eBay is connected on your server, not on the test copy), and the dealer figures against a real dealer's prices.

## 0.13.0

**Sharper where it counts, and ready for push notifications.**

- **The feed opens on what is worth a look.** Buy and Watch listings together, best first. The tabs are **Worth a look**, **Saved** and **Passed**. Listings that turned up since your last visit are marked **New**.
- **Saved has a home.** What you star, or swipe right on a phone, is under the Saved tab.
- **When nothing is worth a look, it says why.** Instead of an empty list you get the most common reason listings were passed, and a button to change what is being looked for.
- **A deal's main button is the thing to do.** On a listing that is fair but not a buy at its price, the button is now **Make an offer**: it opens a message to the seller that is already written, with the amount worked out for you, and **Copy and open the listing** takes you to the ad to paste it. That first message is written by rule and costs nothing; **Write it again** asks the AI.
- **Canadian dollars by themselves.** A new account that says it is in Canada keeps its figures in Canadian dollars from the start. An account that already has history is not changed: Settings does that when you ask.
- **French searches in Quebec.** In Montreal, Quebec City, Gatineau and Sherbrooke, local ads are searched in French first, with English after.
- **Old passed listings clear themselves.** A listing a search brought in that was passed and has been gone from its site for two weeks is deleted, unless you saved it. Anything you added yourself is never touched.
- **Check starts with the camera** on a phone: **Take a photo**, then the photo library.
- **Push notifications, once you add an Apple push key.** Two new options, **Apple push key ID** and **Apple push key**. With both set and alerts turned on in the iPhone app, a listing rated Buy reaches the phone the moment a search finds it. Without them the app checks by itself a few times a day, as before.
- **In the iPhone app (needs the new build from TestFlight):** a count of new listings on the Deals tab, pull down to refresh, and text that follows the phone's text-size setting.

Push has not been sent to a real phone yet: it needs your Apple key and the new app build. The signing of Apple's token is tested; delivery is not. The "Pipeline" page keeps its name for now.

## 0.12.0

**Smarter, and clear about what it costs.**

- **New since you last looked.** When listings rated Buy have turned up since your last visit, the top of the feed shows the best three, each with a **Message** button that goes straight to the note to the seller. When nothing new is a Buy, nothing is shown.
- **The searches tune themselves.** Once a week Coin Machine shows the AI what each of your searches brought in (what was rated Buy or Watch, what you saved, what you dismissed) and lets it drop the words that only brought junk and add the ones that worked. It is one small AI request a week and nothing for you to do.
- **AI: Off, Careful or Full.** Settings now asks one question about the AI instead of a budget and a count: Off (rules only, costs nothing), Careful (the few best new finds, up to about $1 a day) or Full (every promising find, up to about $5 a day). Under it is what the AI cost over the last 7 days, as an estimate. What you start yourself always runs. The old figures are still under Advanced.

Push notifications to the iPhone the moment a Buy is found are not in this release. They need a new app build and an Apple push key that only you can create; they come next.

None of the three has run against the live AI yet: the weekly tuning and the cost line were checked by their rules and tests on a copy with no AI key.

## 0.11.0

**The iPhone look.** The pages are reshaped for a phone, and the iPhone app gets real iPhone controls.

- **Listings lead with the photo.** On a phone each listing is a card with a large photo beside the title, the price call and the expected profit in larger type.
- **Swipe a listing.** On a touch screen, swipe a card right to save it or left to dismiss it. The card names what letting go will do, and nothing happens unless you swipe well past the middle. The card's menu still has the same two.
- **A deal opens on the answer.** On a phone the deal page is the photo, the verdict, what to pay and the one button, plus anything you need to do next. The math, risks, comps, seller and the rest are behind one **Show details** button.
- **Dialogs rise from the bottom** on a phone, full width, like the sheets the phone's own apps use.
- **In the iPhone app (needs the new app build from TestFlight):** the tab bar, the Back button and the More list are now the phone's own controls, floating over the page in Liquid Glass on current iOS (a blurred bar on older iOS). The website's own bottom bar is no longer drawn inside the app. Tabs switch without reloading the page.

The app's new bars were written without an iPhone or simulator to run them on: they compile on GitHub's Macs, and the first look at them is on a real phone through TestFlight. Expect adjustments. The web changes were checked on a phone-sized screen.

## 0.10.0

**The simple version.** One thing to set up, one thing to look at, and a phone screen that opens on listings.

- **One search, not a list of hunts.** Coin Machine now shows a single card, **Looking for**: what you want, how you buy it and where, when it last checked and how many listings are worth a look, with one switch to pause it and a **Change** button. The separate searches still run underneath (each site is searched in its own way), but you never see or manage them. They are under **Advanced** on the Hunts page for anyone curious. If older searches are still running beside it, the card says so and turns them off in one tap.
- **"Near me" now means near you.** Pick your nearest city once and Kijiji is searched within about an hour's drive of it instead of across all of Canada. Local listings show how far away they are ("35 km away"). Facebook Marketplace already uses the location of the Facebook account that is signed in.
- **Set-up is four screens.** The introduction asks who you buy as, the most you would spend on one deal, and what to look for, then starts searching and drops you in the feed while it fills. It no longer asks for profit targets, returns or tax: those are worked out or left at values that work, and are in Settings.
- **The feed opens on listings.** On a phone the first screen is the title, the Looking for card, the Buy / Watch / Pass tabs and listings. Search, sort and filters are behind one button; the figures moved below the list.
- **Four tabs.** Deals, Check (a listing you found yourself), My coins, and More, which holds every other page.
- **Plainer names.** Deal feed is **Deals**, Analyze is **Check a listing**, Lot X-ray is **Value a lot**, Inventory is **My coins**, Melt is **Metal values**, Show kit is **Coin show sheet**, Playbook is **Guide**. Nothing was removed.
- **Samples leave by themselves.** The sample listings and sample hunts are removed the moment you say what to look for.
- **It says what it is doing.** After you answer, the card reads "Searching Kijiji…" and counts what it finds, instead of leaving an empty page.

Checked on a test copy with a real Kijiji search around Toronto. Not yet run on a real account: the AI choosing the searches (0.9.2) and Facebook Marketplace returning listings are still unconfirmed live.

## 0.9.2

**Hunts asks two questions and does the rest.**

- **What do you want to find, and how do you want to buy it?** Tick what you are after (silver bullion, gold, old silver coins, collectible coins, collections and estate lots, or anything underpriced), choose pick up near me, shipped to me, or either, and press **Find deals**. There is one optional line for anything in particular. That is the whole page.
- **The AI chooses the searches.** Claude reads your answers, your goal and the most you spend on one deal, and decides which searches to run on each place that works for you (Kijiji, Reddit, and eBay or Facebook Marketplace once they are connected), in the words sellers on that place actually use, with a price range for each. Coin Machine saves them, runs them straight away and keeps them running. It is one small AI request each time you answer. Without the AI turned on, a built-in list of searches is used instead and the page says so.
- **Change your mind any time.** The page shows what you are looking for and a **Change** button. New answers replace the hunts the last answers made; a hunt you added by hand is never touched.
- **Everything else is under one line, Advanced.** The editor with every setting, the one-keyword box, Facebook sign-in, describing a hunt in your own words, blind spots, the starter hunts and the eBay figures are all still there, folded away.

Not yet checked against the live AI on a real account: the searches it chooses have been read on a test copy only. If a hunt it makes looks wrong, delete it from its row or answer again.

## 0.9.1

Less to set up, less to read, and less spent while nobody is looking.

- **Settings starts with three questions.** What you are doing (buy to resell, buy to keep, stack metal), the most you would spend on one deal, and your currency. Coin Machine works the rest out from those, such as the smallest profit worth showing you as a buy. Everything that was there before is under **Advanced settings**, with the values it already had, for anyone who wants to change one.
- **Hunts starts with one box: "What are you looking for?"** Type it, pick where (Kijiji, Reddit, and eBay or Facebook Marketplace once they are connected), press **Start looking**. How often it runs, what it leaves out and whether the AI reads what it finds are chosen for you, and the first search runs straight away. **New hunt** still opens the editor with every setting.
- **Hunt rows say less.** What it looks for, where, and between which prices, then what it found. The finer settings are in the editor. eBay hunts that cannot run until eBay is connected fold into one line, and the eBay call counts show only once eBay is connected.
- **The AI stops spending when nobody is looking.** Hunts run by themselves, and each run sent its best new finds to the AI, up to a daily cap, whether or not anyone ever opened the app to read them. Now automatic AI analysis rests once Coin Machine has not been opened for a day, and starts again when you open it. Hunts keep running and scoring by rules, which costs nothing. An analysis you start yourself always runs.
- **The daily cap for automatic AI analysis now starts at $2, not $5.** If you set your own cap in Settings it is unchanged. With several accounts sharing your keys, each account has its own cap, and each now rests on its own when its owner is away.
- **Plainer wording.** "This Coin Machine" is gone: it is just Coin Machine.

## 0.9.0

**Coin Machine can now work entirely in Canadian dollars.**

- **One setting: Settings, Costs, Your currency.** Choose **Canadian dollars** and confirm. What you have entered so far (what you paid and sold for, your minimum profit and per-deal limit, want-list limits, hunt price ranges) and every listing are converted once, at the day's rate, and every listing is scored again. From then on every figure you read is in Canadian dollars and every amount you type is too. The top bar shows **CAD**. You can change back the same way.
- **Nothing drifts.** Amounts are converted once, at the switch, not every time a page is drawn: a price you paid stays the price you paid.
- **A Kijiji ad keeps exactly the price it was listed at.** A listing priced in US dollars (eBay, Reddit) is converted when it comes in, and the deal page shows what it said ("US$285.00 as listed").
- **The verdicts are the same deals.** Spot, sold prices, price guides and eBay's fee thresholds are US-dollar figures and are converted at the day's rate when a listing is scored, so a listing gets the same Buy, Watch or Pass in either currency. "Bid up to", "Offer" and the max price are whole Canadian dollars.
- **Hunts.** A hunt's price range is in your currency whatever the marketplace prices in; each marketplace is asked in its own.
- **The AI still reasons in US dollars**, because that is what its knowledge of coin prices is in, and its valuation is converted for you. A message drafted to a seller is written in the currency that seller listed in.
- **Home Assistant** sensors for expected profit and spot report in your currency.
- The rate is a daily reference rate, not a bank's. A US-dollar listing is converted when it is stored or refreshed, so one you captured by hand weeks ago stays at that day's rate until you edit its price.
- Not converted: the notes you typed, the melt tally kept in your browser, and CSV exports, which carry figures in your currency without naming it.
- This has been run against a copy of the app with sample data, switching both ways. It has not yet been run on an account with real history; make a backup first (Settings, Data safety).

## 0.8.1

- **Canadian dollars are now the default.** The option **Currency people here buy in** starts at `CAD`, so an install that never set it switches on this update: prices can be typed in Canadian dollars, Kijiji and Marketplace prices are read as Canadian, and Canadian dollars show beside the figures you act on. An account that chose its own currency in **Settings, Costs** keeps its choice; set the option to `USD` to go back.
- **Signing in to Facebook: the "are you a person" check was blank.** The browser on your Coin Machine may load only Facebook's own addresses, and the check is served from elsewhere, so it never appeared. During a sign-in it is now let through, for you to do yourself in the picture. Coin Machine does not answer it for you. This could not be tried against Facebook's own check before release; if it is still blank, or it is the kind you drag rather than click, say so.
- Coin Machine's own figures, and what you paid and sold for, are still US dollars underneath. Making every figure Canadian is the next piece of work.

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
