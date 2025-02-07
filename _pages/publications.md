---
title: "Publications"
layout: gridlay
sitemap: false
permalink: /publications/
---

{% assign yeartest = true %}
{% for publi in site.data.publications %}
  {% if publi.year %}{% else %}
   {% assign yeartest = false %}
  {% endif %}
{% endfor %}

{% for publi in site.data.publications %}

  {% assign pdfpresent = false %}
  {% if publi.pdf %}
    {% assign pdfpresent = true %}
    {% assign pdffile = publi.pdf %}
  {% endif %}

  {% if publi.year %}{% else %}
  {% assign bibpresent = false %}
  {% if publi.pdf %}
    {% assign bibpresent = true %}
    {% assign bibfile = publi.pdf  | append: ".txt" %}
  {% endif %}

  <div class="well-sm publication-entry">
  <ul class="flex-container">
  <li class="flex-item1">
    {% if publi.image %}
     <img src="{{ site.url }}{{ site.baseurl }}/assets/publications/{{ publi.image }}" class="img-responsive"/>
    {% endif %}
  </li>
  <li class="flex-item2">
    {% if publi.pdf %}<a href="{{ publi.pdf }}" target="_blank">{% endif %} <strong>{{ publi.title }}</strong> {% if publi.pdf %}</a>{% endif %}<br/>
    {{ publi.authors }}<br/>
    <em>{{ publi.venue }}</em><br/>
    {% if publi.abstract %} <a data-bs-toggle="collapse" href="#abstract-{{forloop.index}}"  class="btn-abstract" style="text-decoration:none; color:#ebebeb; hover:#ebebeb;" role="button" aria-expanded="false" aria-controls="abstract-{{forloop.index}}">ABSTRACT</a> {% endif %}
    {% if publi.bib %} <a data-bs-toggle="collapse" href="#bib-{{forloop.index}}"  class="btn-bib" style="text-decoration:none; color:#ebebeb; hover:#ebebeb;" role="button" aria-expanded="false" aria-controls="bib-{{forloop.index}}">BIB</a> {% endif %}
    {% if publi.pdf %}<a href="{{ pdffile }}" target="_blank"><button class="btn-pdf">PDF</button></a>{% endif %}
    {% if publi.doi %}<a href="http://doi.org/{{ publi.doi }}" target="_blank"><button class="btn-doi">DOI</button></a> {% endif %}
    {% if publi.arxiv %}<a href="https://arxiv.org/abs/{{ publi.arxiv }}" target="_blank"><button class="btn-arxiv">ARXIV</button></a> {% endif %}
    {% if publi.code %}<a href="{{ publi.code }}" target="_blank"><button class="btn-code">CODE</button></a> {% endif %}
    {% if publi.suppmat %}<a href="{{ publi.suppmat }}" target="_blank"><button class="btn-suppmat">SUPPLEMENT</button></a> {% endif %}

  {% if publi.abstract %}
  <div class="collapse" id="abstract-{{forloop.index}}"><div class="well-abstract">
   {{publi.abstract}}
  </div></div>
  {% endif %}

  {% if publi.bib %}
  <div class="collapse" id="bib-{{forloop.index}}"><div class="well-bib">```bibtex
{{publi.bib }}
```</div></div>
  {% endif %}

  </li>
  </ul>
  </div>
  {% endif %}
{% endfor %}

{% for myyear in site.data.years %}

{% assign yeartest = false %}
{% for publi in site.data.publications %}
  {% if publi.year == myyear.year %}
   {% assign yeartest = true %}
  {% endif %}
{% endfor %}

{% if site.group_pub_by_year == true %}
{% if yeartest == true %}
### {{ myyear.year }}
{% endif %}
{% endif %}

{% for publi in site.data.publications %}

{% assign pdfpresent = false %}
{% if publi.pdf %}
  {% assign pdfpresent = true %}
  {% assign pdffile = publi.pdf %}
{% endif %}

{% if publi.year == myyear.year %}
{% assign bibpresent = false %}
{% if publi.pdf %}
  {% assign bibpresent = true %}
  {% assign bibfile = publi.pdf  | append: ".txt" %}
{% endif %}

<div class="well-sm publication-entry">
<ul class="flex-container">
<li class="flex-item1">
  {% if publi.image %}
     <img src="{{ site.url }}{{ site.baseurl }}/assets/publications/{{ publi.image }}" class="img-responsive"/>
  {% endif %}
</li>
<li class="flex-item2">
  {% if publi.pdf %}<a href="{{ publi.pdf }}" target="_blank">{% endif %} <strong>{{ publi.title }}</strong>{% if publi.pdf %}</a>{% endif %}<br />
  {{ publi.authors }}<br />
  <em>{{ publi.venue }}</em>{% if publi.year %} ({{publi.year}}){% endif %}<br/>
  {% if publi.abstract %} <a data-bs-toggle="collapse" href="#abstract-{{forloop.index}}"  class="btn-abstract" style="text-decoration:none; color:#ebebeb; hover:#ebebeb; margin-top:5px;" role="button" aria-expanded="false" aria-controls="abstract-{{forloop.index}}">ABSTRACT</a> {% endif %}
  {% if publi.bib %} <a data-bs-toggle="collapse" href="#bib-{{forloop.index}}"  class="btn-bib" style="text-decoration:none; color:#ebebeb; hover:#ebebeb; margin-top:5px;" role="button" aria-expanded="false" aria-controls="bib-{{forloop.index}}">BIB</a> {% endif %}
  {% if publi.pdf %}<a href="{{ pdffile }}" target="_blank"><button class="btn-pdf" style="margin-top:5px;"
  >PDF</button></a>{% endif %}
  {% if publi.doi %}<a href="http://doi.org/{{ publi.doi }}" target="_blank"><button class="btn-doi">DOI</button></a> {% endif %}
  {% if publi.arxiv %}<a href="https://arxiv.org/abs/{{ publi.arxiv }}" target="_blank"><button class="btn-arxiv">ARXIV</button></a> {% endif %}
  {% if publi.code %}<a href="{{ publi.code }}" target="_blank"><button class="btn-code">CODE</button></a> {% endif %}
  {% if publi.suppmat %}<a href="{{ publi.suppmat }}" target="_blank"><button class="btn-suppmat">SUPPLEMENT</button></a> {% endif %}

{% if publi.abstract %}
<br/>
<div class="collapse" id="abstract-{{forloop.index}}"><div class="well-abstract">
 {{publi.abstract}}
</div></div>
{% endif %}

{% if publi.bib %}
<div class="collapse" id="bib-{{forloop.index}}"><div class="well-bib">
{{publi.bib}}
</div></div>
{% endif %}

</li>
</ul>

</div>
{% endif %}
{% endfor %}

{% endfor %}