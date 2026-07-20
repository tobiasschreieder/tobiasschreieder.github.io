<h2 id="publications" style="margin: 2px 0 -15px;">Publications</h2>

<style>
.publication-entry {
  margin-bottom: 32px;
}

.pub-row {
  display: grid;
  grid-template-columns: 240px minmax(0, 1fr);
  column-gap: 28px;
  align-items: start;
}

/* ---------- Image column ---------- */

.publication-image-column {
  width: 240px;
}

.publication-image-box {
  position: relative;

  width: 240px;
  height: 160px;

  display: flex;
  justify-content: center;
  align-items: center;

  padding: 18px;
  box-sizing: border-box;

  background: #ffffff;
  border: 1px solid #ececec;
  border-radius: 4px;

  overflow: hidden;
}

.publication-image {
  width: 100%;
  height: 100%;

  object-fit: contain;
  object-position: center;

  display: block;
}

.publication-badge {
  position: absolute;
  top: 8px;
  left: 8px;
  z-index: 10;

  background: #2E6F40;
  color: #ffffff !important;

  border-radius: 4px;
  padding: 4px 8px;

  font-size: 11px;
  font-weight: 600;
  line-height: 1;
}

/* ---------- Text ---------- */

.publication-text-column {
  min-width: 0;
}

.publication-text-column .title {
  font-size: 1.1em;
  font-weight: 600;
  margin-bottom: 5px;
  line-height: 1.35;
}

.publication-text-column .author {
  margin-bottom: 5px;
  line-height: 1.45;
}

.publication-text-column .periodical {
  margin-bottom: 9px;
  line-height: 1.45;
}

.publication-text-column .links .btn {
  font-size: 12px;
  margin-right: 5px;
}

.publication-text-column .links {
  line-height: 1.8;
}

/* ---------- Mobile ---------- */

@media (max-width: 768px) {

  .pub-row {
    grid-template-columns: 1fr;
    row-gap: 14px;
  }

  .publication-image-column {
    width: 100%;
  }

  .publication-image-box {
    width: 240px;
    height: 160px;
  }

}
</style>

<div class="publications">
<ol class="bibliography">

{% for link in site.data.publications.main %}

<li class="publication-entry">

<div class="pub-row">

<div class="publication-image-column">

{% if link.image %}
<div class="publication-image-box">

<img
src="{{ link.image | relative_url }}"
alt="Preview image for {{ link.title }}"
class="publication-image">

{% if link.conference_short %}
<abbr class="publication-badge">
{{ link.conference_short }}
</abbr>
{% endif %}

</div>
{% endif %}

</div>

<div class="publication-text-column">

<div class="title">
{% if link.pdf %}
<a href="{{ link.pdf }}" target="_blank" rel="noopener">
{{ link.title }}
</a>
{% else %}
{{ link.title }}
{% endif %}
</div>

<div class="author">
{{ link.authors }}
</div>

{% if link.conference %}
<div class="periodical">
<em>{{ link.conference }}</em>
</div>
{% endif %}

<div class="links">

{% if link.pdf %}
<a href="{{ link.pdf }}"
class="btn btn-sm z-depth-0"
target="_blank"
rel="noopener">
PDF
</a>
{% endif %}

{% if link.code %}
<a href="{{ link.code }}"
class="btn btn-sm z-depth-0"
target="_blank"
rel="noopener">
Code
</a>
{% endif %}

{% if link.page %}
<a href="{{ link.page }}"
class="btn btn-sm z-depth-0"
target="_blank"
rel="noopener">
Project Page
</a>
{% endif %}

{% if link.bibtex %}
<a href="{{ link.bibtex }}"
class="btn btn-sm z-depth-0"
target="_blank"
rel="noopener">
BibTeX
</a>
{% endif %}

{% if link.notes %}
<strong>
<i style="color:#e74d3c">{{ link.notes }}</i>
</strong>
{% endif %}

{% if link.others %}
{{ link.others }}
{% endif %}

</div>

</div>

</div>

</li>

{% endfor %}

</ol>
</div>
