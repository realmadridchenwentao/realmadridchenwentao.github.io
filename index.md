---
title: Wentao Chen
layout: home
---

<table border="0" cellpadding="0">
<td valign="top" style="min-width:140px;">
<img src="/assets/mypic.jpg" width="160">
</td>
<td valign="top">
Ph.D. Candidate<br/>
Department of Computer Science<br/>
Shanghai Jiao Tong University<br/>
Office: 478 Gates<br/>
<a href="mailto:zgh23@stanford.edu">wentaochen [at] sjtu [dot] edu [dot] cn</a><br/>
<a href="/assets/GenghanZhang_CV.pdf">Curriculum Vitae</a>
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
xhttp.open("GET", "https://api.github.com/users/zhang677/repos", true);
xhttp.send();
</script>
</td>
</table>


I am a computer science PhD student at Stanford University advised by Professor [Kunle Olukotun](https://engineering.stanford.edu/people/oyekunle-olukotun). I also worked with Professor [Fredrik Kjolstad](https://fredrikbk.com/) on sparse tensor algebra compilation and Professor [Azalia Mirhoseini](http://azaliamirhoseini.com/index.html) on efficient sparse large language models. 

**Research**: My research interests lie in better programming models and systems for domain-specific architectures. I am also interested in optimizing GPU kernels for emerging applications, including sparse and recurrent neural networks.

I graduated from Tsinghua University in 2023 with a bachelor degree in Eletronic Engineering. At Tsinghua, I did research at [NICS-EFC Lab](https://nicsefc.ee.tsinghua.edu.cn/) on effcient sparse tensor algebra for GPU and [IDEAL Lab](https://github.com/tsinghua-ideal) on kernel architecture search.

<h2 class="tableheading">Selected Publications</h2>

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
          {%- if author == "genghan" %}
            <b><font color="#000000">{{ site.data.authors[author].name }}</font></b>
          {%- else %}
            <a href="{{- site.data.authors[author].site -}}" style="color: #464646">{{ site.data.authors[author].name }}</a>
          {%- endif -%}
          {%- if forloop.last == false and forloop.length > 2 -%}
            ,
          {%- endif %}
        {%- endfor -%}<br/>
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

<h2 class="tableheading">Talks</h2>
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
</table>