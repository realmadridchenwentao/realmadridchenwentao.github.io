---
title: Wentao Chen
layout: home
---

<table border="0" cellpadding="0">
<td valign="top" style="min-width:140px;">
<img src="/assets/cwt.jpg" width="240">
</td>
<td valign="top">
Ph.D. Candidate<br/>
Electrical and Computer Engineering<br/>
Global College<br/>
Shanghai Jiao Tong University<br/>
<a href="mailto:wentaochen@sjtu.edu.cn">wentaochen [at] sjtu [dot] edu [dot] cn</a><br/>
<!-- <a href="/assets/cv.pdf">Curriculum Vitae</a> -->
<div id=siteUpdate> </div>
<script>
const desiredRepo = "realmadridchenwentao.github.io"
const monthNames = ["January", "February", "March", "April", "May", "June",
  "July", "August", "September", "October", "November", "December"
];

var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    let repos = JSON.parse(this.responseText);
    repos.forEach((repo)=>{
      if (repo.name == desiredRepo)
      {
        var lastUpdated = new Date(repo.pushed_at);
        var day = lastUpdated.getUTCDate();
        var month = lastUpdated.getUTCMonth();
        var year = lastUpdated.getUTCFullYear();
        siteUpdate.innerHTML += (`<em>Site Last Updated ${monthNames[month]} ${year}</em><br>`);
      }
    });
  }
};
xhttp.open("GET", "https://api.github.com/users/realmadridchenwentao/repos", true);
xhttp.send();
</script>
</td>
</table>

I am a Ph.D. candidate at [Global College](https://www.ji.sjtu.edu.cn/), [Shanghai Jiao Tong University](https://www.sjtu.edu.cn/). My advisor is Prof. [An Zou](https://sites.gc.sjtu.edu.cn/zouan/). Previously, I worked with Prof. [Weimin Zhou](https://optics.arizona.edu/person/weimin-zhou) from [University of Arizona](https://www.arizona.edu/). I received my B.E. degree from [Beijing University of Posts and Telecommunications](https://www.bupt.edu.cn/) in 2023, where I fortunately worked with Prof. [Qicheng Lao](https://scholar.google.com/citations?user=cwKb6FwAAAAJ), Prof. [Kongming Liang](https://scholar.google.com/citations?user=dmlkJR4AAAAJ), and Prof. [Zhanyu Ma](https://zhanyuma.cn/).


**Research**: My research interests lie in designing scalable and self-improving AI systems for high-performance computing, including better programming models and systems for domain-specific architectures, as well as optimizing GPU kernels for emerging applications. [[Awesome-LLM4Kernel](https://github.com/fanqiNO1/Awesome-LLM4Kernel)] [[KernelPilot](https://www.kernelpilot.com/)] [[CUDABench](https://github.com/CUDA-Bench/CUDABench)]

Previously, my research was dedicated to exploring mathematical principles of image science, explores modern AI/ML technologies, and utilizes a wide variety of computational tools to advance image formation, perception, and interpretation, including deep generative models for medical image analysis, AI/ML-based image perception and observer designs for objective assessment of image quality, as well as task-oriented image acquisition, reconstruction, and enhancement.

I am always open to research collaborations. Feel free to contact me.


<h2 class="tableheading">Publications</h2>

<table border="0">
  {% for pub_keyval in site.data.publications %}
    <tr>
      {%- assign pub = pub_keyval[1] -%}
      <td>
        <b><a href="pub_md/{{pub_keyval[0]}}.html" style="color: #464646">{{ pub.title }}</a></b><br/>
        {%- for author in pub.authors -%}
          {%- if forloop.last == true and forloop.length > 1 %}
            and
          {%- endif %}
          {%- if author == "wentaochen" %}
            <b><font color="#000000">{{ site.data.authors[author].name }}</font></b>
            {%- if pub.co_first_authors and pub.co_first_authors contains author -%}<sup>†</sup>{%- endif -%}
          {%- else %}
            <a href="{{- site.data.authors[author].site -}}" style="color: #464646">{{ site.data.authors[author].name }}</a>
            {%- if pub.co_first_authors and pub.co_first_authors contains author -%}<sup>†</sup>{%- endif -%}
          {%- endif -%}
          {%- if forloop.last == false and forloop.length > 2 -%}
            ,
          {%- endif %}
        {%- endfor -%}<br/>
        {%- if pub.co_first_authors -%}
        <span style="font-size: 0.9em; color: #666">† co-first author</span><br/>
        {%- endif -%}
        <i>{{ pub.venue }}
        {%- if pub.venuenote %}
        ({{ pub.venuenote }})
        {%- endif -%}
        {%- if pub.volume -%}
        , Volume {{ pub.volume }}
        {%- endif -%}
        {%- if pub.issue -%}
        , Issue {{ pub.issue }}
        {%- endif -%}
        </i>, {{ pub.month }} {{ pub.year }}<br/>
        {%- if pub.award -%}
          <span style="color:#0096FF"><b>{{ pub.award }}</b></span><br/>
        {%- endif -%}
      </td>
      <td valign="top" width="20">
        {% if pub.pdf %}
            <a href="{{ pub.pdf }}"><img src="/assets/PDF_icon.svg" alt="pdf" /></a>
	{% elsif pub.url %}
            <a href="{{ pub.url }}"><img src="/assets/PDF_icon.svg" alt="pdf" /></a>
        {% endif %}
        {% if pub.movie %}
          <a href="{{ pub.movie }}"><img src="/assets/movie.png" alt="youtube" /></a>
        {% endif %}
      </td>
    </tr>
{% endfor %}
</table>

<!-- <h2 class="tableheading">Talks</h2>
<table border="0">
{%- for talk_keyval in site.data.talks %}
  {%- assign talk= talk_keyval[1] -%}
  <tr>
  <td> 
    <b>
    {% if talk.url %}
	<a href="{{talk.url}}">{{talk.title}}</a></b>
    {%- else %}
    {{talk.title}}</b>
    {%- endif -%}
	<br/>{{talk.month}} {{talk.year}} 
    <br/>{{talk.venue}}
    <td valign="top" width="20">
    {% if talk.movie %}
      <a href="{{ talk.movie }}"><img src="/assets/movie.png" alt="youtube" /></a>
    {% endif %}
    </td>
  </td>
  </tr>
{% endfor %}
</table>

<h2 class="tableheading">Blogs</h2>
<table border="0">
  {% for blog_keyval in site.data.blogs %}
    {% assign blog = blog_keyval[1] %}
    {% assign blog_path = "blog_md/" | append: blog.filename | append: ".md" %}
    {% for page in site.pages %}
      {% if page.path == blog_path %}
        <tr>
          <td>
            <b><a href="{{ page.url | relative_url }}" style="color: #464646">{{ page.title }}</a></b><br/>
            {% if page.authors %}
              {% for author in page.authors %}
                {% if forloop.last == true and forloop.length > 1 %}
                  and
                {% endif %}
                <a href="{{site.data.authors[author].site}}" style="color: #464646">{{ site.data.authors[author].name }}</a>
                {% if forloop.last == false and forloop.length > 2 %}
                  ,
                {% endif %}
              {% endfor %}<br/>
            {% endif %}
            <i>{{ page.date | date: "%B %d, %Y" }}</i>
          </td>
        </tr>
      {% endif %}
    {% endfor %}
  {% endfor %}
</table> -->

<h2 class="tableheading">Teaching</h2>
At Shanghai Jiao Tong University:
- ECE6501G, Principles of Medical Imaging, Graduate Course TA (Spring 2024).
- ECE7609J, Principles of Imaging Science, Graduate Course TA (Summer 2023).
- VE445/ECE4450J, Introduction to Machine Learning, Undergraduate Course TA (Fall 2022, Fall 2023).
- VE490, Undergraduate Research, Undergraduate Course TA (Fall 2022).


<h2 class="tableheading">Miscellaneous</h2>
- An ENTJ. I love traveling and reading books.
- A Real Madrid & DFB fan, also a railway & aviation enthusiast. 
- My hometown is [Huainan](https://en.wikipedia.org/wiki/Huainan), a prefecture-level city in north-central Anhui province, China. It is known for its coal industry and thermal power plants. It is also considered to be the hometown and birthplace of tofu.
