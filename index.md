---
layout:   default
---

<!-- Automatic Slideshow Images -->
<div class="mySlides slidesIndex w3-display-container w3-center">
  <img src="/public/img/front-1.jpg" style="width:100%">
  <div class="w3-display-bottommiddle w3-container w3-text-white w3-padding-32 w3-hide-small">
  </div>
</div>

<!-- Menu Container -->
<div class="w3-container">
  <div class="w3-content w3-padding-32" style="max-width:700px">
    <h2 class="w3-wide w3-center w3-padding-32">最新消息</h2>
    <div class="w3-row w3-center w3-card-2 w3-padding">
      <a href="javascript:void(0)" onclick="openMenu(event, 'News');" id="myLink">
        <div class="w3-col s6 tablink">新聞</div>
      </a>
      <a href="javascript:void(0)" onclick="openMenu(event, 'Games');">
        <div class="w3-col s6 tablink">賽程</div>
      </a>
    </div>

    <div id="News" class="w3-container menu w3-padding-48 w3-card-2">
      {% assign news = (site.news | sort: 'date') %}
      {% for new in news reversed %}
      <h5>{{ new.date | date: "%Y-%m-%d" }} {{ new.title }}</h5>
      <p class="w3-text-grey">{{ new.subtitle }}</p>
      <a onclick="myFunction('{{ new.index }}')"><i class="fa fa-chevron-circle-down fa-lg" aria-hidden="true"></i></a><br>
      <div id="{{ new.index }}" class="w3-container w3-hide">
        <p>{{ new.content }}</p>
      </div>
      {% endfor %}
    </div>

    <div id="Games" class="w3-container menu w3-padding-48 w3-card-2">
      <p>尚未出爐！</p>
    </div>  
  </div>
</div>


<script>
// Automatic Slideshow - change image every 4 seconds
var myIndex = 0;
carousel();

function carousel() {
    var i;
    var x = document.getElementsByClassName("slidesIndex");
    for (i = 0; i < x.length; i++) {
       x[i].style.display = "none";
    }
    myIndex++;
    if (myIndex > x.length) {myIndex = 1}
    x[myIndex-1].style.display = "block";
    setTimeout(carousel, 4000);
}
</script>
