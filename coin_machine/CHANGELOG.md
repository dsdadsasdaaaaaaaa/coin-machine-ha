# Changelog

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
