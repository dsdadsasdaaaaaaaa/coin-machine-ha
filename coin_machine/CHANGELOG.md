# Changelog

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
