<h2 id="publications" style="margin: 2px 0 -15px;">Publications</h2>

<style>
.publication-entry {
  margin-bottom: 32px;
}

.pub-row {
  display: grid;
  grid-template-columns: 180px minmax(0, 1fr);
  column-gap: 24px;
  align-items: start;
}

/* Fixed column for every publication image */
.publication-image-column {
  position: relative;
  width: 180px;
}

/* Fixed white canvas */
.publication-image-box {
  position: relative;
  box-sizing: border-box;

  width: 180px;
  height: 125px;

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 14px;

  background: #ffffff;
  border: 1px solid #eeeeee;
  border-radius: 3px;
  overflow: hidden;
}

/* Scale image down while preserving the complete image */
.publication-image {
  display: block;

  width: 100%;
  height: 100%;

  object-fit: contain;
  object-position: center;

  background: #ffffff;
}

/* Conference badge in the upper-left corner */
.publication-image-box .publication-badge {
  position: absolute;
  top: 7px;
  left: 7px;
  z-index: 2;

  display: inline-block;
  padding: 3px 7px;

  color: #ffffff !important;
  background-color: #2e6f40 !important;

  border: none;
  border-radius: 3px;

  font-size: 11px;
  font-weight: 600;
  line-height: 1.2;
  text-decoration: none;
  white-space: nowrap;
}

/* Text column */
.publication-text-column {
  min-width: 0;
}

.publication-text-column .title {
  margin-bottom: 5px;
  font-size: 1.08em;
  font-weight: 600;
  line-height: 1.35;
}

.publication-text-column .author {
  margin-bottom: 5px;
  line-height: 1.45;
}

.publication-text-column .periodical {
  margin-bottom: 9px;
  line-height: 1.4;
}

.publication-text-column .links {
  line-height: 1.8;
}

.publication-text-column .links .btn {
  margin-right: 4px;
  font-size: 12px;
}

/* Mobile layout */
@media screen and (max-width: 700px) {
  .pub-row {
    grid-template-columns: 1fr;
    row-gap: 14px;
  }

  .publication-image-column {
    width: 180px;
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
            <abbr
              class="publication-badge"
              title="{{ link.conference_short }}">
              {{ link.conference_short }}
            </abbr>
            {% endif %}

          </div>

          {% elsif link.conference_short %}
          <abbr
            class="publication-badge"
            title="{{ link.conference_short }}">
            {{ link.conference_short }}
          </abbr>
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
            <a
              href="{{ link.pdf }}"
              class="btn btn-sm z-depth-0"
              target="_blank"
              rel="noopener">
              PDF
            </a>
            {% endif %}

            {% if link.code %}
            <a
              href="{{ link.code }}"
              class="btn btn-sm z-depth-0"
              target="_blank"
              rel="noopener">
              Code
            </a>
            {% endif %}

            {% if link.page %}
            <a
              href="{{ link.page }}"
              class="btn btn-sm z-depth-0"
              target="_blank"
              rel="noopener">
              Project Page
            </a>
            {% endif %}

            {% if link.bibtex %}
            <a
              href="{{ link.bibtex }}"
              class="btn btn-sm z-depth-0"
              target="_blank"
              rel="noopener">
              BibTeX
            </a>
            {% endif %}

            {% if link.notes %}
            <strong>
              <i style="color: #e74d3c;">
                {{ link.notes }}
              </i>
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
