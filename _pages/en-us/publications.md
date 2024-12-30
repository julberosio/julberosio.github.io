---
page_id: publications
layout: page
permalink: /publications/
title: publications
description:

sections:
#  - bibquery: "@article"
#    text: "Non-academic publications"
  - bibquery: "@misc|@phdthesis|@mastersthesis"
    text: " "
  - bibquery: "@InProceedings|@online"
    text: " "

years: [2023, 2022, 2021, 2020, 2019, 2018, 2017]
nav: true
nav_order: 3
---
All of my published research articles are available through S&P Global's Capital IQ Pro platform (requires subscription): <a href="https://www.capitaliq.spglobal.com">[link]</a>.

Abridged versions of my selected research articles are available for public viewing here: <a href="https://www.spglobal.com/marketintelligence/contributors/115275/julber-osio">[link]</a>.

<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <p class="bibtitle">{{section.text}}</p>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      <h2 class="year">{{y}}</h2>
      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>
