+++
title = "Minimal demo"
template = "index.html"
+++

## What we're aiming for:

1. `code`, *em* and **strong** in the summary are preserved
2. Markdown doesn't wrap the summary text in a `<p>` (shown in red), which [isn't valid in phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)
3. Zola converts the relative image link to absolute so that it'll work in a feed

Adding a CSS rule `summary p { display: inline; }` will paper over the layout disturbance, but it'll still be Technically Incorrect, which is arguably the worst kind of incorrect.

## Using a Markdown shortcode

This gets its `<summary>` content wrapped in a `<p>`, but at least Zola can make the colocated asset link absolute.

{% details_md(summary="Summary using `code`, *emphasis*, **strong** and so on") %}
Blah blah large bowl of porridge blah blah
![test image](test.jpg)
Blah blah lemon curry blah blah
{% end %}

If we change the shortcode to insert no whitespace internally, we don't get a `<p>` because we don't get processed at all.

{% details_md_oneliner(summary="Summary using `code`, *emphasis*, **strong** and so on") %}
Blah blah large bowl of porridge blah blah
![test image](test.jpg)
Blah blah lemon curry blah blah
{% end %}

## Using an HTML shortcode

This also gets its `<summary>` content wrapped in a `<p>`, plus the asset link stays relative.

{% details_html(summary="Summary using `code`, *emphasis*, **strong** and so on") %}
Blah blah large bowl of porridge blah blah
![test image](test.jpg)
Blah blah lemon curry blah blah
{% end %}

And a oneliner variant with no internal whitespace comes out just the same.

{% details_html_oneliner(summary="Summary using `code`, *emphasis*, **strong** and so on") %}
Blah blah large bowl of porridge blah blah
![test image](test.jpg)
Blah blah lemon curry blah blah
{% end %}

## UPDATE! - golden Markdown solution, using ky-bean's `markdown(inline=true)` tip

{% details_md_golden(summary="Summary using `code`, *emphasis*, **strong** and so on") %}
Blah blah large bowl of porridge blah blah
![test image](test.jpg)
Blah blah lemon curry blah blah
{% end %}