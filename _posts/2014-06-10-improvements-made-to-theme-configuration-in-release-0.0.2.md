---
layout: post
category : general
tags : [release, dr-henry, v0.0.2]
---
{% include setup %}
## Minor release, less confusing theme configuration

Themes are now completely controled by the _data/themes.yml file. This combines the per-theme files in v0.0.1 and adds dependency information. The setup include now calculates the dependency information so it does not need to be explicitly declared.

Just set the theme you want as the depends to the "local" theme, to set which theme you want. (And setup your overrides as you make them.)

Read on if you care about the nitty gritty details, or ignore them if you don't. :smile:

<!--fold-->

I couldn't go quite as far as I had wanted in precalculating theme config. By iterating the list of core theme items, and evaluating the final template path, we could build an index of theme items, and not need to do the double include for the theme include mechanism. Instead we could say: {% capture text %}|.% include theme_map[yourtheme]  %.|{% endcapture %}{% include {{tt_liquid_raw}} %}
<br/>
The main benefit to this, is it would let us freely use the key=value expressions for include-specific details. We can't do that with the middle include, as it would need to pass everything else on.

However... liquid templates do not allow for creation of anything but strings, and with some creativity, arrays. The dependency loader builds it's array by creating a pipe delimited string, and running it through a split filter.

We could make every theme declare every item, be it it's own or from another theme. Pros to this, you could mix and match however, no depenency lines. Cons, what's the point of any depenency tracking at that point, and a lot wordier config.

So, we keep the double include for themes for now.

