# News debloater (anti-attention seekers)
## Removes sidebar articles and other "recommended articles"

### Add the list
[Subscribe here for uBlock Origin](https://subscribe.adblockplus.org/?location=https://raw.githubusercontent.com/I-I-IT/News-sidebard-and-related-article-remover/refs/heads/main/filters.txt&title=News_debloater)

If it doesn't work, you can add the following link to your extension (only uBlock Origin on Firefox will work for all filters): 
[https://raw.githubusercontent.com/I-I-IT/News-sidebard-and-related-article-remover/refs/heads/main/filters.txt](https://raw.githubusercontent.com/I-I-IT/News-sidebard-and-related-article-remover/refs/heads/main/filters.txt)
uBlock Origin filter removing news websites features to keep you reading, including "Trending Topics", "top stories", etc.

### Notes & contributions
Feel free to contribute. For now, goal is only to remove bloat in reading pages, not in the homepage itself.

I only use cosmetic filters, but if you have know-how on network filters, feel free to add some. I now use css selectors, so this might add a bit of load. If you PC doesn't have OK-ish compute, this might mean page load will be slower.

Feel free to open a PR adding new filters.

### Do I remove in-article links to other articles ?

No I don't. Although it affects the reading experience, as the reading experience is no longer linear but a trace between metalinks. What you can do however, is change the color of links from blue to grey. You could even put those links in the same color as text. To change the colors on Firefox, follow this guide. https://support.mozilla.org/en-US/kb/change-fonts-and-colors-websites-use

### What don't I remove ?

Donation prompts, article tags, pictures, videos, author information, prompts for anonymous sources.

### Do I remove newsletters prompts ?

I generally do, although if it's very discreet and non-intrusive I might let it.

### How to create filters yourself ?

I personally started by using the uBlock element picker, but this has several drawbacks. Nowadays, sites often name their div class name not only by their function, but they add an unique id. So instead of div class="recommendations-sidebar" we get div class="recommendations-sidebar 73vryf4". This means that if you use the Picker, the site can just change this id per article or every day, and your picker becomes useless. The other drawbacks of the picker is that if the site doesn't have a class name for an element, it will just see that this the div number 5 (nth-of-type 5) and block that element. That mean at best your filter will not work on a shorter article, but at worst it will break the site on a longer article.

So instead it is preferable to use a combination of css-selectors and uBo's has() and has-text().

has-text() is useful for sites that will insert divs or title (h2, h3, h4) for recommendation without any class. So you can just write h3:has-text(/Recommendation/). Replace Recommendation by actual text they use, such as "Recommended articles". 

In some cases, the div will not have an useful class name, but it will have another property with an useful name. For example it might be div class="euu472" data-parsely="recommendations-sidebar". In this case use class[data-parsely="recommendations-sidebar"]. You might also want to add :has-text() after, just to be sure it is actually a recommendations. If it's ambiguous, always use has-text to make sure you aren't hiding normal content.

### Why not just use Firefox's Reading Mode ?

Firefox's reading mode doesn't remove recommendations, although it often makes them ugly. You can still use it on top of the filters to have a more minimalist experience.


### Example
This represents the more subtle changes as I already have almost a dozen distraction blocklists. See https://github.com/collinbarrett/FilterLists/pull/4806#issue-3036720546

