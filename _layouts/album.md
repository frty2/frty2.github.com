<!doctype html>
<!--[if lt IE 7]><html class="no-js lt-ie9 lt-ie8 lt-ie7" lang="en"> <![endif]-->
<!--[if (IE 7)&!(IEMobile)]><html class="no-js lt-ie9 lt-ie8" lang="en"><![endif]-->
<!--[if (IE 8)&!(IEMobile)]><html class="no-js lt-ie9" lang="en"><![endif]-->
<!--[if gt IE 8]><!--> <html class="no-js" lang="en"><!--<![endif]-->
<head>
{% include head.html %}
</head>

<body id="page" {% if page.image.feature %}class="feature"{% endif %}>

{% include browser-upgrade.html %}
{% include navigation.html %}

{% if page.image.feature %}
<div class="entry-header">
  {% if page.image.credit %}<div class="image-credit">Image source: <a href="{{ page.image.creditlink }}">{{ page.image.credit }}</a></div><!-- /.image-credit -->{% endif %}
  <div class="entry-image">
    <img src="{{ site.url }}/images/{{ page.image.feature }}" alt="{{ page.title }}">
  </div><!-- /.entry-image -->
</div><!-- /.entry-header -->
{% endif %}

<div id="main" role="main">
  <article class="hentry">
    <header class="header-title">
      <div class="header-title-wrap">
        <h1 class="entry-title">{{ page.title }}</h1>
        {% if site.reading_time %}
        <p class="entry-reading-time">
          <i class="fa fa-clock-o"></i>
          {% assign readtime = content | number_of_words | divided_by:site.words_per_minute %}
          Reading time ~{% if readtime <= 1 %}1 minute{% else %}{{ readtime }} minutes{% endif %}
        </p><!-- /.entry-reading-time -->
        {% endif %}
      </div><!-- /.header-title-wrap -->
    </header>
    <div class="entry-content">
      {% if page.albumid %}
      <iframe style="border: 0; width: 350px; height: 621px;" src="http://bandcamp.com/EmbeddedPlayer/album={{ page.albumid }} /size=large/bgcol=ffffff/linkcol=de270f/transparent=true/" seamless></iframe>
      {% endif %}
      <br />
      {% if page.facebook %}
        <a href="{{ page.facebook }}" target="_blank">Facebook</a> -
      {% endif %}

      {% if page.myspace %}
        <a href="{{ page.myspace }}" target="_blank">Myspace</a> - 
      {% endif %}

      {% if page.bandcamp %}
        <a href="{{ page.bandcamp }}" target="_blank">Bandcamp</a> - 
      {% endif %}

      {{ content }}
      <footer class="entry-meta">
        <span class="entry-tags">{% for tag in page.tags %}<a href="{{ site.url }}/tags/#{{ tag }}" title="Pages tagged {{ tag }}" class="tag inpost">#{{ tag }}</a>{% unless forloop.last %}{% endunless %}{% endfor %}</span>
        {% if page.modified %}<span>Updated on <span class="entry-date date published updated"><time datetime="{{ page.modified }}">{{ page.modified | date: "%B %d, %Y" }}</time></span></span>
        <span class="author vcard"><span class="fn">{{ site.owner.name }}</span></span>{% endif %}
        {% if page.share != false %}{% include social-share.html %}{% endif %}
      </footer>
    </div><!-- /.entry-content -->
    {% if page.comments != false %}<section id="disqus_thread"></section><!-- /#disqus_thread -->{% endif %}
  </article>
</div><!-- /#main -->

<div class="footer-wrapper">
  <footer role="contentinfo">
    {% include footer.html %}
  </footer>
</div><!-- /.footer-wrapper -->

{% include scripts.html %}          

</body>
</html>
