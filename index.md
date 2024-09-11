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
          <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span> | <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
    <div class="separator">
        <hr>
    </div>
  </section>
{% endfor %}