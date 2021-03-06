---
layout: main
---

<main class="home" id="post" role="main" itemscope="itemscope" itemtype="http://schema.org/Blog">
    <div id="grid" class="row flex-grid">
    {% for post in site.posts %}
        <article class="box-item" itemscope="itemscope" itemtype="http://schema.org/BlogPosting" itemprop="blogPost">
            <span class="category">
                <a href="{{ site.url }}{{ site.baseurl }}/categoria/{{ post.category | slugify | replace: 'ê', 'e' }}">
                    <span>{{ post.category }}</span>
                </a>
            </span>
            <div class="box-body">
                {% if post.image %}
                    <div class="cover">
                        {% include new-post-tag.html date=post.date %}
                        <a href="{{ post.url | prepend: site.baseurl }}" {%if isnewpost %}class="new-post"{% endif %}>
                            <meta itemprop="image" content="{{ post.image }}">
                            <img src="assets/img/placeholder.png" data-url="{{ post.image }}" class="preload">
                        </a>
                    </div>
                {% endif %}
                <div class="box-info">
                    <meta itemprop="datePublished" content="{{ post.date | date_to_xmlschema }}">
                    <time itemprop="datePublished" datetime="{{ post.date | date_to_xmlschema }}" class="date">
                        {% include date.html date=post.date format="%d de %B de %Y" lang="pt" %}
                    </time>
                    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                        <h2 class="post-title" itemprop="name">
                            {{ post.title }}
                        </h2>
                    </a>
                    <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                        <p class="description" itemprop="headline">{{ post.introduction }}</p>
                    </a>
                    <div class="tags">
                        {% for tag in post.tags %}
                            <a href="{{ site.baseurl}}/tags/#{{tag | slugify }}"><span itemprop="keywords">{{ tag }}</span></a>
                        {% endfor %}
                    </div>
                    <span style="display:none;" itemprop="author" itemtype="http://schema.org/Person" itemscope="">
                        <meta itemprop="name" content="{{ site.author }}">
                    </span>
                    <span style="display:none;" itemprop="publisher" itemtype="http://schema.org/Organization" itemscope="">
                        <meta itemprop="name" content="{{ site.author }}">
                        <img itemprop="logo" src="assets/img/blog-image.png" />
                    </span>
                </div>
            </div>
        </article>
    {% endfor %}
    </div>
</main>
