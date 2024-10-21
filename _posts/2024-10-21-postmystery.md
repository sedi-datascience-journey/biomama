---
layout: post
title: "The Case of the Disappearing Post"
date: 2024-10-21
categories: Tutorials
---


The Case of the Disappearing Post
==================================

I was beyond frustrated. My very first blog post just wouldn't show up! I tried everything---redoing each step, reviewing my process over and over---but still, nothing. It was like the post was playing a game of hide and seek! After all my troubleshooting, I finally figured out what was going wrong. Here's a checklist I went through to solve the mystery:

Step 1: The Magic of Front Matter ✨
-----------------------------------

Every Jekyll post needs something called "front matter" at the very top of the Markdown file. This little block of text is what Jekyll uses to recognize it as a blog post. I double-checked for any extra spaces or typos, making sure it looked something like this:


```yaml
layout: post
title: "Welcome to BioMama"
date: 2024-10-14
categories: introduction
```

*Tip:* The front matter should always include `layout`, `title`, and `date` at the very least.

Step 2: Review the Site URL 🔍
------------------------------

Next, I made sure I was looking at the right website address and refreshing the page properly. It might sound obvious, but it's an easy thing to overlook.

Step 3: Check the Post Filename 📝
----------------------------------

The file name was the next suspect. It needs to follow a strict naming convention:


```css
`YYYY-MM-DD-title-of-the-post.md`
```

For example, my file was named `2024-10-14-welcome-to-biomama.md`. But here's the catch---if the date is set in the future, the post won't appear until that date arrives!

Step 4: Verify Jekyll Build Settings ⚙️
---------------------------------------

Sometimes, changes take a few minutes to show up on GitHub Pages. I double-checked that the `_posts` folder was at the root of my repository and that my `_config.yml` file was set up correctly, just in case I had a custom configuration.

* * * * *

Well, despite checking all these steps, my post was still missing! It felt like I was chasing a ghost. 😫

In a last-ditch effort, I tried adding a `default.html` file in the `_layouts` folder. Here's the code I used:

```html
<!doctype html>
<html lang="{{ site.lang | default: "en-US" }}">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">

  {% seo %}
  <link rel="stylesheet" href="{{ '/assets/css/style.css?v=' | append: site.github.build_revision | relative_url }}">
  <script src="{{ '/assets/js/scale.fix.js' | relative_url }}"></script>
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <!--[if lt IE 9]>
  <script src="//html5shiv.googlecode.com/svn/trunk/html5.js"></script>
  <![endif]-->
  {% include head-custom.html %}
</head>
<body>
  <div class="wrapper">
    <header>
      <h1 class="header">{{ site.title | default: site.github.repository_name }}</h1>
      <p class="header">{{ site.description | default: site.github.project_tagline }}</p>

      <ul>
        {% if site.show_downloads %}
          <li class="download"><a class="buttons" href="{{ site.github.zip_url }}">Download ZIP</a></li>
          <li class="download"><a class="buttons" href="{{ site.github.tar_url }}">Download TAR</a></li>
        {% endif %}
        <li><a class="buttons github" href="{{ site.github.repository_url }}">View On GitHub</a></li>
      </ul>

      {% if site.github.is_project_page %}
        <p class="header">This project is maintained by <a class="header name" href="{{ site.github.owner_url }}">{{ site.github.owner_name }}</a></p>
      {% endif %}

      {% if site.github.is_user_page %}
        <ul>
          <li><a class="buttons github" href="{{ site.github.owner_url }}">GitHub Profile</a></li>
        </ul>
      {% endif %}
    </header>

    <section>
      {{ content }}
    </section>

    <!-- Blog Section -->
    <section class="blog-section">
      <h2>Blog</h2>
      <ul class="post-list">
        {% for post in site.posts %}
          <li>
            <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
            <p>{{ post.excerpt }}</p>
            <p><small>{{ post.date | date: "%B %d, %Y" }}</small></p>
          </li>
        {% endfor %}
      </ul>
    </section>

    <footer>
      <p><small>Hosted on <a href="https://pages.github.com">GitHub Pages</a> using the Dinky theme</small></p>
    </footer>
  </div>
  <!--[if !IE]><script>fixScale(document);</script><![endif]-->
</body>
</html>

```

And... still nothing. My first post was determined to stay invisible!

* * * * *

The Unexpected Solution 🎉
--------------------------

With a sigh, I tried changing the post's file name to something simpler: `2024-10-14-welcome.md`. And guess what? It worked! It seems like the filename format needs to be just `YYYY-MM-DD-title.md` with only three dashes allowed. My elusive first post finally showed up!

While I solved the mystery, my blog still looked a little chaotic. I clearly needed to learn more about Markdown to make it shine. But that's a topic for another post---stay tuned for some Markdown magic next time!