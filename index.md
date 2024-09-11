---
layout: default
---

<header>
  <h1>./ {{ site.title }}</h1>
  <p>{{ site.description }}</p>
</header>

<section>
  <h2>Latest posts:</h2>
  <ul>
    {% for post in site.posts limit:5 %}
      <li>
        <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span> | <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
</section>

{% for tag in site.tags %}
  <section>
    ---
    ---
    <h2>Tags {{ tag[0] }}:</h2>
    <ul>
      {% for post in tag[1] %}
        <li>
          <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span> | <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ul>
  </section>
{% endfor %}