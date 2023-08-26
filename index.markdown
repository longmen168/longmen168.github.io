---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
toc: true
comments: true
---

![日月光华学术沙龙](https://raw.githubusercontent.com/longmen168/longmen168.github.io/main/images/blog.jpg)

<div class="search-container">
  <input type="text" id="search-input" placeholder="search blog posts...">
  <ul id="results-container"></ul>
</div>

<!--script src="https://unpkg.com/simple-jekyll-search/dest/simple-jekyll-search.min.js"></script-->
<script src="/js/simple-jekyll-search.min.js"></script>

<script>
	window.simpleJekyllSearch = new SimpleJekyllSearch({
	searchInput: document.getElementById('search-input'),
	resultsContainer: document.getElementById('results-container'),
	json: '/search.json',
	searchResultTemplate: '<li><a href="{url}?query={query}" title="{desc}">{title}</a></li>',
	noResultsText: 'No results found',
	limit: 10,
	fuzzy: false,
	exclude: ['Welcome']
  })
</script>

<div class="posts">
  {% for post in paginator.posts %}
  {% unless post.draft %}
    <article class="post">
      <h1>
        <a href="./{{ post.url }}">{{ post.title }}</a>
      </h1>

      <div clsss="meta">
        <span class="date">
          {{ post.date | date: "%Y-%m-%d" }}
        </span>

        <ul class="tag">
          {% for tag in post.tags %}
          <li>
            <a href="./tags#{{ tag }}">
              {{ tag }}
            </a>
          </li>
          {% endfor %}
        </ul>
      </div>

      <div class="entry">
        {{ post.excerpt | truncate: 200 }}
      </div>

      <a href="/{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endunless %}
  {% endfor %}
</div>

<div class="pagination">
  {% if paginator.previous_page %}
    <span class="prev">
      <a href="/{{ paginator.previous_page_path }}" class="prev">
        ← 上一页
      </a>
    </span>
  {% endif %}
  {% if paginator.next_page %}
    <span class="next">
      <a href="/{{ paginator.next_page_path }}" class="next">
        下一页 →
      </a>
    </span>
  {% endif %}
</div>

<!--不蒜子网站访客统计-->
<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js">
</script>
<!-- pv的方式，单个用户连续点击n篇文章，记录n次访问量 -->
<div align="center">
	<span id="busuanzi_container_site_pv" style="font-family:Consolas;color:Red;font-size:12px;">
		View:<span id="busuanzi_value_site_pv" style="font-family:Consolas;color:Red;font-size:12px;"></span>
	</span>
	<!-- uv的方式，单个用户连续点击n篇文章，只记录1次访客数 -->
	<span id="busuanzi_container_site_uv" style="font-family:Consolas;color:Red;font-size:12px;">
		User:<span id="busuanzi_value_site_uv" style="font-family:Consolas;color:Red;font-size:12px;"></span>
	</span>
</div>