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
      <ul class="w3-ul">
      {% assign news = (site.news | sort: 'date') %}
      {% for new in news reversed %}
      <li>
      <h5>{{ new.date | date: "%Y-%m-%d" }} {{ new.title }}</h5>
      <p class="w3-text-grey">{{ new.subtitle }}</p>
      <a class="w3-btn w3-white w3-border" onclick="myFunction('{{ new.index }}')">查看更多</a><br>
      <div id="{{ new.index }}" class="w3-container w3-hide">
        <p>{{ new.content }}</p>
      </div>
      <br>
      </li>
      {% endfor %}
      </ul>
    </div>

    <div id="Games" class="w3-container menu w3-padding-48 w3-card-2">
      <table class="w3-table w3-striped">
        <tr>
          <td>時間</td>
          <td>活動內容</td>
        </tr>
        <tr>
          <td>12:30</td>
          <td>開放進場</td>
        </tr>
        <tr>
          <td>13:00</td>
          <td>場邊活動及攤販開始</td>
        </tr>
        <tr>
          <td>13:15</td>
          <td>開場典禮</td>
        </tr>
        <tr>
          <td>13:30</td>
          <td>賽前表演、開球、球員進場</td>
        </tr>
        <tr>
          <td>14:00</td>
          <td>上半場比賽：1~4局</td>
        </tr>
        <tr>
          <td></td>
          <td>中場 - 外野擲準大賽、抽獎</td>
        </tr>
        <tr>
          <td></td>
          <td>下半場比賽 - 5~7局</td>
        </tr>
        <tr>
          <td></td>
          <td>賽後 - 頒獎、抽獎</td>
        </tr>
      </table>
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

// When the user clicks anywhere outside of the modal, close it
var modal = document.getElementById('ticketModal');
window.onclick = function(event) {
  if (event.target == modal) {
    modal.style.display = "none";
  }
}

// Tabbed Menu
function openMenu(evt, menuName) {
  var i, x, tablinks;
  x = document.getElementsByClassName("menu");
  for (i = 0; i < x.length; i++) {
     x[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablink");
  for (i = 0; i < x.length; i++) {
     tablinks[i].className = tablinks[i].className.replace(" w3-theme-d3", "");
  }
  document.getElementById(menuName).style.display = "block";
  evt.currentTarget.firstElementChild.className += " w3-theme-d3";
}
document.getElementById("myLink").click();

// collapse
function myFunction(id) {
    var x = document.getElementById(id);
    if (x.className.indexOf("w3-show") == -1) {
        x.className += " w3-show";
    } else {
        x.className = x.className.replace(" w3-show", "");
    }
}

</script>
