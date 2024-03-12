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

<!-- {% include_relative includes/pub_short.md %} -->

# 📝 Selected Publications 
{% include_relative pubs/2024-CVPR-SPDMLR.md %}
<!-- {% include_relative includes/pubs/2024-ICLR-LieBN.md %}
{% include_relative includes/pubs/2023-AAAI-RieLocal.md %}
{% include_relative includes/pubs/2021-TBD-Hbrid.md %} --> 

{% include_relative includes/honers.md %}

{% include_relative includes/others.md %}

<!-- <a href="https://info.flagcounter.com/UTQG"><img src="https://s11.flagcounter.com/mini/UTQG/bg_FFFFFF/txt_000000/border_CCCCCC/flags_0/" alt="Flag Counter" border="0"></a> -->
