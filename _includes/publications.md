<h2 id="publications" style="margin: 2px 0 -15px;">Publications</h2>

<style>
.publication-entry {
  margin-bottom: 30px;
}

.pub-row {
  display: grid;
  grid-template-columns: 180px 1fr;
  column-gap: 24px;
  align-items: start;
}

.publication-image-column {
  width: 180px;
}

.publication-image-box {
  width: 180px;
  height: 120px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 8px;
}

.publication-image {
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
  object-fit: contain;
}

.publication-text-column {
  min-width: 0;
}

.publication-text-column .title {
  font-size: 1.08em;
  font-weight: 600;
  margin-bottom: 4px;
}

.publication-text-column .author {
  margin-bottom: 4px;
  line-height: 1.4;
}

.publication-text-column .periodical {
  margin-bottom: 8px;
  line-height: 1.4;
}

.publication-text-column .links .btn {
  font-size: 12px;
  margin-right: 4px;
}

@media (max-width: 700px) {
  .pub-row {
    grid-template-columns: 1fr;
  }

  .publication-image-column {
    width: 100%;
    margin-bottom: 12px;
  }

  .publication-image-box {
    width: 220px;
    height: 140px;
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
              class="publication-image teaser img-fluid z-depth-1">
          </div>
          {% endif %}

          {% if link.conference_short %}
          <abbr class="badge">{{ link.conference_short }}</abbr>
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
