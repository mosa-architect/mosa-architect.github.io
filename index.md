---
layout: page
title: MOSAアーキテクト技術ブログ
description: MOSAアーキテクトの技術ブログです。技術に関することなら何でも書いています。

---
{% include JB/setup %}


<div>
  <img src="img/mosa-blog.png" alt="猛者技術ブログ" style="width:100%;" />
</div>
<div class="container-fluid" style="margin-top:60px;">
  <div class="row">
    <div class="col-lg-6 col-md-6 col-sm-6 col-xs-12">
<h3>記事リスト</h3>
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
    </div>
    <div class="col-lg-6 col-md-6 col-sm-6 col-xs-12">
<h3>ブロガーリスト</h3>
<ul class="tag_box">
  {% assign categories_list = site.categories %}  
  {% include JB/categories_list %}
</ul>
    </div>
  </div>
</div>




