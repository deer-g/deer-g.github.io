---
layout: default
---
<section>
  <h2>Latest posts:</h2>
  <ul>
    {% for post in site.posts limit:5 %}
      <li>
        <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span> | <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
  <div class="separator">
    <hr>
  </div>
</section>

{% for tag in site.tags %}
  <section>
    <h2>Tags {{ tag[0] }}:</h2>
    <ul>
      {% for post in tag[1] %}
        <li>
          <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <span class="post-separator">|</span>
          <a href="{{ post.url | relative_url }}" class="post-link" title="{{ post.title }}">
            {% if post.title.size > 70 %}
              {{ post.title | truncate: 67 }}
            {% else %}
              {{ post.title }}
            {% endif %}
          </a>
        </li>
      {% endfor %}
    </ul>
    <div class="separator">
        <hr>
    </div>
  </section>
{% endfor %}