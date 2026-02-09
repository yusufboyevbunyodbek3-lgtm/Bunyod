anime-site/
│── index.html        (bosh sahifa)
│── watch.html        (anime ko‘rish)
│── admin.html        (admin panel)
│
│── css/
│   └── style.css
│
│── js/
│   ├── app.js        (anime chiqarish)
│   ├── watch.js      (qismlar)
│   └── admin.js      (admin panel)<!DOCTYPE html>
<html>
<head>
  <title>Anime Site</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>

<h1>🔥 Anime World</h1>
<div id="anime-list"></div>

<script src="js/app.js"></script>
</body>
</html>fetch("https://YOUR_FIREBASE_URL/anime.json")
.then(res => res.json())
.then(data => {
  let html = "";
  for (let id in data) {
    html += `
      <div class="card">
        <h3>${data[id].name}</h3>
        <a href="watch.html?id=${id}">Ko‘rish</a>
      </div>`;
  }
  document.getElementById("anime-list").innerHTML = html;
});<h2 id="title"></h2>

<iframe id="player" width="100%" height="480"></iframe>

<div id="episodes"></div>

<script src="js/watch.js"></script>const id = new URLSearchParams(location.search).get("id");

fetch(`https://YOUR_FIREBASE_URL/anime/${id}.json`)
.then(res => res.json())
.then(data => {
  document.getElementById("title").innerText = data.name;

  let eps = "";
  data.episodes.forEach((ep, i) => {
    eps += `<button onclick="play('${ep}')">${i+1}-qism</button>`;
  });

  document.getElementById("episodes").innerHTML = eps;
  document.getElementById("player").src = data.episodes[0];
});

function play(url){
  document.getElementById("player").src = url;
}<h2>Admin Panel</h2>

<input id="name" placeholder="Anime nomi">
<textarea id="episodes" placeholder="Video linklar (har qatorga bittadan)"></textarea>
<button onclick="save()">Saqlash</button>

<script src="js/admin.js"></script>function save(){
  const name = document.getElementById("name").value;
  const eps = document.getElementById("episodes").value.split("\n");

  fetch("https://YOUR_FIREBASE_URL/anime.json", {
    method: "POST",
    body: JSON.stringify({
      name: name,
      episodes: eps
    })
  });

  alert("Anime qo‘shildi!");
}https://drive.google.com/file/d/VIDEO_ID/previewhttps://username.github.io/anime-site
