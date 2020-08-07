https://news.ycombinator.com/item?id=24067840#24073947

I'm having a very hard time rationalizing these numbers. Something has to have some very poor assumptions:

Let's assume each page load is ~1mbit, and it's being served from 1000km away. 1mbit may be low, but most of it will presumably be content delivered by a CDN which is far closer than 1000km.

The reference design (which I work on) for 400G DWDM systems are ~100W for 2 transceivers + EDFA + switches, for a standard 80km link. Assuming we hop every 80km (which should be conservative here), we get 3mJ for the energy through the network. The previous generation is probably 10x worse, so ~30mJ.

Let's add the endpoint too; Wifi router + cable modem (12W or rather 3W marginal power since it's running anyway/ 200mbit) = 15mJ

And finally for the server. I'd hope the server could do 1k requests per second, and that should amortize against backends, etc (2k RPS, but frontend + DB backend server, maybe), maybe 150W for the server, so 150mJ.

This gives us 200mJ for a page load. Using California's current (1:28am) emissions for power generation of 0.274 mT/MWh (it's 1/3rd of this during the day), this yields 15ug/request.

Where do the remaining 5 orders of magnitude come from? What am I missing? If TCO/production energy of the server was included, that couldn't more than double it (capex in a datacenter < opex, and if 100% of the server cost was for energy, we could double, but this is wildly conservative) 
