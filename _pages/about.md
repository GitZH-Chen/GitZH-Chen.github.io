---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

# "天地有正气，杂然赋流形 -- 文天祥"

{% include_relative includes/intro.md %}

{% include_relative includes/news.md %}

{% include_relative includes/overview.md %}

{% include_relative includes/pub_short.md %}

{% include_relative includes/honers.md %}

{% include_relative includes/others.md %}

<!-- <script type="text/javascript" id="clstr_globe" src="//clustrmaps.com/globe.js?d=ykPbI30LsamiuG9mdkAJKZzccIjf7o4rxc-dBMXGY20"></script> -->


<!-- <a href="https://info.flagcounter.com/UTQG"><img src="https://s11.flagcounter.com/mini/UTQG/bg_FFFFFF/txt_000000/border_CCCCCC/flags_0/" alt="Flag Counter" border="0"></a> -->