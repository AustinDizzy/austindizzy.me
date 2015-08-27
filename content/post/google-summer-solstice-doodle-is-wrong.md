+++
date = "2015-08-03T00:16:03-04:00"
draft = false
title = "Google's Summer Solstice Doodle is Wrong"
tags = ["google", "summer solstice", "google doodle", "wrong", "physics", "visible electromagnetic spectrum"]
slug = "google-summer-solstice-doodle-is-wrong"
+++

*NOTE*: [Originally written on Medium](https://medium.com/@austindizzy/google-s-summer-solstice-doodle-is-wrong-358373d18587)

Of all companies you’d think to put an unnecessary amount of detail into even the smallest things, [Google](https://google.com) would’ve probably been on that list. However, they got the 2015 Summer Solstice Google Doodle wrong! *GASP*.

How did they get it wrong, exactly? Seems like they forgot about how the [visible electromagnetic spectrum](https://en.wikipedia.org/wiki/Electromagnetic_spectrum) works.

{{< figure src="https://cdn-images-1.medium.com/max/600/1*_540KqlwX2jNkj01TCPDtA.png" title="Visible Electromagnetic Spectrum chart" >}}

Shown by this visible spectrum graph, red is the fastest color yet has the least amount of photon energy — the amount of energy a single photon can carry among a particular spectral electromagnetic wavelength and frequency.

To understand why how much energy each photon carries matters, we must first understand basic spectroscopy — or, “[How Do We See Color?](https://www.youtube.com/watch?v=l8_fZPHasdo)”

Basically, the gist is this: when you’re seeing a red object, that object is actually absorbing all the other colors and reflecting only red light. That reflected red light enters your corneas and you perceive the object as being red. This principle should be common knowledge for anyone who’s taken high school physics, if you read any articles about [#thedress](http://www.theguardian.com/science/head-quarters/2015/feb/27/the-dress-blue-black-white-gold-vision-psychology-colour-constancy), or [if you’ve ever seen a sunset](http://news.psu.edu/story/141337/2007/03/05/research/probing-question-what-gives-sunrise-and-sunset-its-orange-glow).

So if a red popsicle were to reflect only the color red and absorb every other color, the energies of the photons would be absorbed by the popsicle as heat due to the first law of thermodynamics and the law of conservation of energy. Absorbing all those higher energy photons in a closed system would introduce energy into the red popsicle(s) faster than any other spectral color popsicle.

So, in order to comply with the laws of physics, the red popsicle should begin melting first. After that, yellow, green, and blue in that order. In a more specific order, the larger blue popsicle should begin melting last as its mass is greater than the other popsicles.

# Unnecessary Details

Just to go into unnecessary details, as Google typically would’ve, let’s dive into the enthalpic heat of fusion in thermodynamics.

Water has a latent heat of fusion of 334.774 joules per gram. Using the table above, we find the sum of the photon energies for the colors except for red is 11.52 to 12.78 electronvolts (eV). 1 electronvolt is equivalent to 1.6*10^(-19) joules. So as you can see, it’s going to take quite a lot more than a few photons of each color light to melt even a noticably nominal amount of a red popsicle.

For our play along calculations, we’ll use the [U.S. Department of Agriculture’s Nutrient Database for Standard Reference](http://ndb.nal.usda.gov/) to find the weight of the consumable part of one popsicle, which is 33 grams. We’ll also say that to “begin” to melt (i.e. start dripping, like featured in the doodle), it has to lose at least 5% of its consumable mass. So to melt 1.65 grams of popsicle, we’d need 552.3771 (1.65g * 334.774J/g) joules of energy; in electronvolts, that’s 3.447667*10^(21) eV.

Since the red object absorbs all but red light, the popsicle absorbs an average of 12.15 eV per photon. So finally, to get the 3.447667*10^(21) eV of energy required to melt the 1.65 grams of the popsicle at an average 12.15 eV per photon, it’d require ~2.837*10^(20) photons.

Recycling this method and applying it for each color, assuming each popsicle is of equal mass except for the larger blue popsicle — having double mass — gives us the following:

* Smaller blue: ~3.038*10^(20) photons
* Larger blue: ~6.075*10^(20) photons
* Yellow: ~2.912*10^(20) photons
* Green: ~2.962*10^(20) photons

Hopefully we all know light travels at a constant speed in this system, so we can just order the colors based on the number of photons required to melt the sample. So the order would be, as it should be: red, yellow, green, smaller blue, then larger blue.

As a closing note, a handful of things were assumed here: the popsicles were brought into the sun at the same exact time, were removed from the same freezer both at the same temperature and time, neither popsicle is nominally closer to the sun or above the horizon than the other, etc. This post was just to poke a little fun at Google, get familiar with writing on Medium, and just because I felt the need write something.

---

For a second closing note, please keep in mind I'm just a college student and I neither major in nor have ever taken a college course in physics. This is just my understanding from high school AP Physics. So if I get a few small details wrong, I'd love to know where and am open to comments.
