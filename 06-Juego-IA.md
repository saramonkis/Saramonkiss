---
layout: default
title: Juego IA
nav_order: 6
permalink: /06-juego-ia/
---

# Gatitos Galácticos

En esta práctica se desarrolló un videojuego con **HTML, CSS y JavaScript** utilizando Inteligencia Artificial como apoyo. El juego se puede jugar directamente en esta página.

**Controles:** WASD o flechas para moverse y **barra espaciadora** para disparar o seleccionar opciones.

<div id="gg-wrap">
  <div id="gg-top">
    <div>
      <strong>Gatitos Galácticos ✦</strong>
      <span>Defiende Miau-9</span>
    </div>
    <div class="gg-controls">WASD / Flechas · ESPACIO</div>
  </div>

  <div id="gg-game">
    <canvas id="gg-canvas" width="960" height="540"></canvas>

    <div id="gg-hud" class="gg-hidden">
      <span>❤ <b id="gg-lives">3</b></span>
      <span>✦ <b id="gg-score">0</b></span>
      <span>Oleada <b id="gg-wave">1</b></span>
      <span id="gg-boss-hud" class="gg-hidden">Rattus <i><em id="gg-boss-life"></em></i></span>
    </div>

    <div id="gg-overlay">
      <div id="gg-panel">
        <p id="gg-kicker">PLANETA MIAU-9</p>
        <h2 id="gg-title">Gatitos Galácticos</h2>
        <p id="gg-text">Defiende el planeta de una invasión de ratas espaciales.</p>
        <div id="gg-menu"></div>
        <div id="gg-custom" class="gg-hidden"></div>
        <p id="gg-hint">W/S o ↑/↓ para elegir · ESPACIO para aceptar</p>
      </div>
    </div>

    <div id="gg-toast" class="gg-hidden"></div>
  </div>
</div>

## Descripción

El videojuego tiene dos modos. En el **modo historia** se explica que las ratas llegaron a Miau-9 diciendo que eran una raza rechazada y exiliada que quería recuperar lo que había perdido. Más adelante se descubre que fueron los humanos quienes originalmente les quitaron sus territorios, pero el jefe final, **Almirante Rattus**, revela que la invasión actual ya no es por eso, sino porque le gusta conquistar y controlar otros planetas.

En el **modo libre** solamente se trata de sobrevivir, derrotar ratas y obtener la mayor cantidad de puntos posible.

También se puede **personalizar el gatito** antes de jugar escogiendo diferentes colores y accesorios.

<style>
#gg-wrap{
  margin:1.5rem 0 2rem;
  color:#fffafc;
  font-family:system-ui,-apple-system,"Segoe UI",sans-serif;
}
#gg-top{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:12px;
  padding:12px 14px;
  border-radius:16px 16px 0 0;
  background:linear-gradient(90deg,#25134d,#4f1b65);
  border:1px solid #ffffff22;
}
#gg-top strong{display:block;font-size:1.15rem;color:#ffd2ea}
#gg-top span{font-size:.8rem;color:#cfc6e5}
.gg-controls{
  font-size:.78rem;
  padding:7px 10px;
  border-radius:999px;
  background:#ffffff12;
  color:#d9d1ea;
}
#gg-game{
  position:relative;
  width:100%;
  aspect-ratio:16/9;
  overflow:hidden;
  border-radius:0 0 18px 18px;
  background:#090a1f;
  border:1px solid #ffffff22;
  border-top:0;
  box-shadow:0 18px 50px #0004;
}
#gg-canvas{display:block;width:100%;height:100%}
#gg-overlay{
  position:absolute;
  inset:0;
  display:grid;
  place-items:center;
  padding:20px;
  background:linear-gradient(#08091855,#080918d6);
  backdrop-filter:blur(4px);
}
#gg-panel{
  width:min(680px,94%);
  padding:clamp(20px,4vw,34px);
  border:1px solid #ffffff24;
  border-radius:24px;
  background:#131333e8;
  box-shadow:0 18px 55px #0006;
}
#gg-kicker{
  margin:0 0 6px;
  color:#9ff3ff;
  font-size:.72rem;
  font-weight:900;
  letter-spacing:.14em;
}
#gg-title{
  margin:0;
  color:#fff;
  font-size:clamp(1.8rem,5vw,3.5rem);
  line-height:1;
}
#gg-text{color:#cdc6df;line-height:1.55;margin:15px 0}
#gg-menu{display:grid;gap:8px}
.gg-item,.gg-row{
  padding:12px 14px;
  border-radius:14px;
  border:1px solid #ffffff18;
  background:#ffffff0c;
}
.gg-item{font-weight:800;cursor:pointer;user-select:none}
.gg-item.gg-selected{
  transform:translateX(7px);
  border-color:#ff9dcec0;
  background:linear-gradient(90deg,#ff9dce3c,#b9a7ff24);
}
#gg-custom{display:grid;gap:9px}
.gg-row{display:flex;justify-content:space-between;gap:12px}
.gg-row b{color:#ffd2ea}
#gg-hint{margin:15px 0 0;color:#aaa4bc;font-size:.82rem}
#gg-hud{
  position:absolute;
  left:14px;right:14px;top:12px;
  display:flex;gap:8px;align-items:center;
  pointer-events:none;
}
#gg-hud>span{
  padding:6px 10px;
  border-radius:999px;
  border:1px solid #ffffff25;
  background:#09091faa;
  backdrop-filter:blur(8px);
  font-size:.82rem;
  font-weight:800;
}
#gg-boss-hud{
  margin-left:auto;
  display:flex!important;
  align-items:center;
  gap:8px;
  min-width:220px;
}
#gg-boss-hud i{
  height:7px;
  flex:1;
  border-radius:999px;
  overflow:hidden;
  background:#ffffff20;
}
#gg-boss-hud em{
  display:block;
  width:100%;
  height:100%;
  background:linear-gradient(90deg,#ff9dce,#ff4e97);
}
#gg-toast{
  position:absolute;
  left:50%;bottom:18px;
  transform:translateX(-50%);
  max-width:calc(100% - 30px);
  padding:9px 14px;
  border-radius:999px;
  background:#09091fdd;
  border:1px solid #ffffff28;
  font-weight:800;
  text-align:center;
}
.gg-hidden{display:none!important}
@media(max-width:700px){
  #gg-top{align-items:flex-start;flex-direction:column}
  #gg-hud{flex-wrap:wrap}
  #gg-boss-hud{min-width:48vw}
}
</style>

<script>
(function () {
  "use strict";

  var canvas = document.getElementById("gg-canvas");
  var ctx = canvas.getContext("2d");
  var W = canvas.width;
  var H = canvas.height;

  var overlay = document.getElementById("gg-overlay");
  var menu = document.getElementById("gg-menu");
  var custom = document.getElementById("gg-custom");
  var kicker = document.getElementById("gg-kicker");
  var title = document.getElementById("gg-title");
  var text = document.getElementById("gg-text");
  var hint = document.getElementById("gg-hint");
  var hud = document.getElementById("gg-hud");
  var livesEl = document.getElementById("gg-lives");
  var scoreEl = document.getElementById("gg-score");
  var waveEl = document.getElementById("gg-wave");
  var bossHud = document.getElementById("gg-boss-hud");
  var bossLife = document.getElementById("gg-boss-life");
  var toast = document.getElementById("gg-toast");

  var skins = [
    ["Rosa cosmico", "#ff9fd2", "#fff0f8"],
    ["Azul nebulosa", "#80dfff", "#e9fbff"],
    ["Lila lunar", "#b9a7ff", "#f1edff"],
    ["Naranja solar", "#ffb36b", "#fff0de"],
    ["Menta estelar", "#7ee6c2", "#ecfff8"],
    ["Cafe meteorito", "#b98a6d", "#f8e8dc"]
  ];
  var accessories = ["Mono estelar", "Casco espacial", "Visor corazon", "Corona lunar", "Sin accesorio"];

  var skin = 0;
  var acc = 0;
  var state = "menu";
  var mode = "story";
  var selected = 0;
  var score = 0;
  var lives = 3;
  var wave = 1;
  var spawnTimer = 0;
  var waveTimer = 0;
  var last = 0;
  var inv = 0;
  var boss = null;
  var storyPart = 0;
  var storyIndex = 0;
  var keys = {};

  var bullets = [];
  var enemies = [];
  var enemyBullets = [];
  var stars = [];
  var player = {x: W / 2, y: H - 65, w: 52, h: 42, speed: 310, cooldown: 0};

  for (var si = 0; si < 110; si++) {
    stars.push({
      x: Math.random() * W,
      y: Math.random() * H,
      r: 0.5 + Math.random() * 1.5,
      s: 8 + Math.random() * 18
    });
  }

  var story1 = [
    ["CAPITULO 1", "La invasion", "Miau-9 era un planeta tranquilo hasta que aparecieron naves de ratas espaciales."],
    ["TRANSMISION RATA", "Venimos por lo que nos quitaron", "Las ratas dicen que fueron rechazadas, exiliadas y expulsadas de sus antiguos hogares."],
    ["MISION", "Defiende Miau-9", "Usa WASD o las flechas para moverte y ESPACIO para disparar."]
  ];

  var story2 = [
    ["ARCHIVO ANTIGUO", "La historia estaba incompleta", "Los registros muestran que fueron humanos quienes quitaron a las ratas sus antiguos territorios y recursos."],
    ["ALERTA", "Rattus se acerca", "Miau-9 no participo en aquella guerra, pero las ratas siguen atacando."]
  ];

  var story3 = [
    ["JEFE FINAL", "Almirante Rattus", "Rattus revela que ahora coloniza otros planetas porque quiere conquistarlos, aunque quienes les quitaron todo originalmente fueron los humanos."],
    ["ULTIMA MISION", "Protege Miau-9", "Derrota a Rattus y evita que la injusticia se repita contra otro planeta."]
  ];

  var menuOptions = [
    {label:"Modo historia", action:function(){ beginStory(); }},
    {label:"Modo libre", action:function(){ startGame("free"); }},
    {label:"Personalizar gatito", action:function(){ openCustom(); }},
    {label:"Controles", action:function(){ showControls(); }}
  ];

  function preventGameKeys(e) {
    var k = e.key.toLowerCase();
    if (k === " " || k.indexOf("arrow") === 0 || k === "w" || k === "a" || k === "s" || k === "d") {
      e.preventDefault();
    }
  }

  document.addEventListener("keydown", function(e) {
    preventGameKeys(e);
    var k = e.key.toLowerCase();
    keys[k] = true;

    if (state === "menu") {
      if (k === "w" || k === "arrowup") {
        selected = (selected + menuOptions.length - 1) % menuOptions.length;
        renderMenu();
      } else if (k === "s" || k === "arrowdown") {
        selected = (selected + 1) % menuOptions.length;
        renderMenu();
      } else if (k === " " || k === "enter") {
        menuOptions[selected].action();
      }
    } else if (state === "custom") {
      if (k === "a" || k === "arrowleft") {
        skin = (skin + skins.length - 1) % skins.length;
        renderCustom();
      } else if (k === "d" || k === "arrowright") {
        skin = (skin + 1) % skins.length;
        renderCustom();
      } else if (k === "w" || k === "arrowup") {
        acc = (acc + accessories.length - 1) % accessories.length;
        renderCustom();
      } else if (k === "s" || k === "arrowdown") {
        acc = (acc + 1) % accessories.length;
        renderCustom();
      } else if (k === " " || k === "enter" || k === "escape") {
        showMenu();
      }
    } else if (state === "story") {
      if (k === " " || k === "enter") {
        nextStory();
      }
    } else if (state === "controls" || state === "over" || state === "win") {
      if (k === " " || k === "enter" || k === "escape") {
        showMenu();
      }
    }
  });

  document.addEventListener("keyup", function(e) {
    keys[e.key.toLowerCase()] = false;
  });

  function showMenu() {
    state = "menu";
    selected = 0;
    overlay.classList.remove("gg-hidden");
    hud.classList.add("gg-hidden");
    custom.classList.add("gg-hidden");
    menu.classList.remove("gg-hidden");
    kicker.textContent = "PLANETA MIAU-9";
    title.textContent = "Gatitos Galacticos";
    text.textContent = "Defiende el planeta de una invasion de ratas espaciales.";
    hint.textContent = "Haz clic en una opcion o usa W/S - Flechas - ESPACIO";
    renderMenu();
  }

  function renderMenu() {
    menu.innerHTML = "";
    for (var i = 0; i < menuOptions.length; i++) {
      (function(index) {
        var d = document.createElement("div");
        d.className = "gg-item" + (index === selected ? " gg-selected" : "");
        d.textContent = menuOptions[index].label;
        d.setAttribute("role", "button");
        d.setAttribute("tabindex", "0");
        d.addEventListener("click", function() {
          selected = index;
          menuOptions[index].action();
        });
        d.addEventListener("keydown", function(e) {
          if (e.key === "Enter" || e.key === " ") {
            e.preventDefault();
            menuOptions[index].action();
          }
        });
        menu.appendChild(d);
      })(i);
    }
  }

  function openCustom() {
    state = "custom";
    menu.classList.add("gg-hidden");
    custom.classList.remove("gg-hidden");
    kicker.textContent = "TALLER DE MODA ESPACIAL";
    title.textContent = "Personaliza tu gatito";
    text.textContent = "Elige pelaje y accesorio.";
    hint.textContent = "A/D o Flechas: pelaje - W/S: accesorio - ESPACIO: guardar";
    renderCustom();
  }

  function renderCustom() {
    custom.innerHTML = "";
    var r1 = document.createElement("div");
    r1.className = "gg-row";
    r1.innerHTML = "<b>Pelaje</b><span>" + skins[skin][0] + "</span>";
    var r2 = document.createElement("div");
    r2.className = "gg-row";
    r2.innerHTML = "<b>Accesorio</b><span>" + accessories[acc] + "</span>";
    var r3 = document.createElement("div");
    r3.className = "gg-row";
    r3.innerHTML = "<b>Guardar</b><span>ESPACIO</span>";
    custom.appendChild(r1);
    custom.appendChild(r2);
    custom.appendChild(r3);
  }

  function showControls() {
    state = "controls";
    menu.classList.add("gg-hidden");
    custom.classList.add("gg-hidden");
    kicker.textContent = "CONTROLES";
    title.textContent = "Solo teclado";
    text.innerHTML = "<b>WASD o flechas:</b> mover al gatito.<br><b>ESPACIO:</b> disparar o aceptar.";
    hint.textContent = "ESPACIO para volver";
  }

  function beginStory() {
    mode = "story";
    storyPart = 1;
    storyIndex = 0;
    showStory(story1);
  }

  function showStory(arr) {
    state = "story";
    overlay.classList.remove("gg-hidden");
    hud.classList.add("gg-hidden");
    menu.classList.add("gg-hidden");
    custom.classList.add("gg-hidden");
    var s = arr[storyIndex];
    kicker.textContent = s[0];
    title.textContent = s[1];
    text.textContent = s[2];
    hint.textContent = "ESPACIO para continuar";
  }

  function nextStory() {
    var arr = storyPart === 1 ? story1 : (storyPart === 2 ? story2 : story3);
    storyIndex++;
    if (storyIndex < arr.length) {
      showStory(arr);
      return;
    }
    if (storyPart === 1) {
      startGame("story");
    } else if (storyPart === 2) {
      state = "play";
      overlay.classList.add("gg-hidden");
      hud.classList.remove("gg-hidden");
    } else {
      state = "play";
      overlay.classList.add("gg-hidden");
      hud.classList.remove("gg-hidden");
      createBoss();
    }
  }

  function startGame(m) {
    mode = m;
    state = "play";
    score = 0;
    lives = 3;
    wave = 1;
    spawnTimer = 0;
    waveTimer = 0;
    inv = 0;
    boss = null;
    bullets.length = 0;
    enemies.length = 0;
    enemyBullets.length = 0;
    player.x = W / 2;
    player.y = H - 65;
    overlay.classList.add("gg-hidden");
    hud.classList.remove("gg-hidden");
    updateHud();
    if (m === "free") {
      say("Modo libre: resiste todo lo que puedas");
    }
  }

  function createBoss() {
    enemies.length = 0;
    enemyBullets.length = 0;
    boss = {x:W/2,y:105,w:150,h:95,hp:55,max:55,t:0,cd:0};
    updateHud();
    say("JEFE FINAL: Almirante Rattus");
  }

  function updateHud() {
    livesEl.textContent = lives;
    scoreEl.textContent = score;
    waveEl.textContent = wave;
    if (boss) {
      bossHud.classList.remove("gg-hidden");
      bossLife.style.width = Math.max(0, boss.hp / boss.max * 100) + "%";
    } else {
      bossHud.classList.add("gg-hidden");
    }
  }

  function spawnEnemy() {
    var type = "normal";
    var r = Math.random();
    if (wave >= 3 && r > 0.8) type = "tank";
    else if (wave >= 2 && r > 0.6) type = "zig";
    var e = {x:50+Math.random()*(W-100),y:-35,w:42,h:34,hp:1,s:72+wave*8,t:Math.random()*6,type:type};
    if (type === "tank") { e.w = 58; e.h = 44; e.hp = 3; e.s *= 0.7; }
    if (type === "zig") e.hp = 2;
    enemies.push(e);
  }

  function shoot() {
    bullets.push({x:player.x,y:player.y-28,r:5,s:520});
    player.cooldown = 0.18;
  }

  function damage() {
    if (inv > 0 || state !== "play") return;
    lives--;
    inv = 1;
    updateHud();
    if (lives <= 0) gameOver();
  }

  function gameOver() {
    state = "over";
    overlay.classList.remove("gg-hidden");
    hud.classList.add("gg-hidden");
    kicker.textContent = "MISION FALLIDA";
    title.textContent = "Game Over";
    text.textContent = "Puntaje final: " + score;
    hint.textContent = "ESPACIO para volver";
  }

  function victory() {
    state = "win";
    overlay.classList.remove("gg-hidden");
    hud.classList.add("gg-hidden");
    kicker.textContent = "MIAU-9 ESTA A SALVO";
    title.textContent = "Victoria galactica";
    text.textContent = "Derrotaste al Almirante Rattus con " + score + " puntos.";
    hint.textContent = "ESPACIO para volver";
  }

  function storyProgress() {
    if (mode !== "story") return;
    if (storyPart === 1 && score >= 450) {
      storyPart = 2;
      storyIndex = 0;
      showStory(story2);
    } else if (storyPart === 2 && score >= 1000) {
      storyPart = 3;
      storyIndex = 0;
      showStory(story3);
    }
  }

  function rectCircle(r, c) {
    var cx = Math.max(r.x-r.w/2, Math.min(c.x, r.x+r.w/2));
    var cy = Math.max(r.y-r.h/2, Math.min(c.y, r.y+r.h/2));
    var dx = c.x-cx, dy = c.y-cy;
    return dx*dx+dy*dy < c.r*c.r;
  }

  function overlap(a,b) {
    return Math.abs(a.x-b.x) < (a.w+b.w)/2 && Math.abs(a.y-b.y) < (a.h+b.h)/2;
  }

  function update(dt) {
    for (var s=0; s<stars.length; s++) {
      stars[s].y += stars[s].s*dt;
      if (stars[s].y > H) { stars[s].y = -2; stars[s].x = Math.random()*W; }
    }

    if (state !== "play") return;

    inv = Math.max(0, inv-dt);
    player.cooldown = Math.max(0, player.cooldown-dt);

    var mx=0,my=0;
    if (keys["a"] || keys["arrowleft"]) mx--;
    if (keys["d"] || keys["arrowright"]) mx++;
    if (keys["w"] || keys["arrowup"]) my--;
    if (keys["s"] || keys["arrowdown"]) my++;
    if (mx && my) { mx*=0.707; my*=0.707; }

    player.x += mx*player.speed*dt;
    player.y += my*player.speed*dt;
    player.x = Math.max(32, Math.min(W-32, player.x));
    player.y = Math.max(H*0.45, Math.min(H-35, player.y));

    if (keys[" "] && player.cooldown <= 0) shoot();

    if (!boss) {
      spawnTimer -= dt;
      waveTimer += dt;
      if (spawnTimer <= 0) {
        spawnEnemy();
        spawnTimer = Math.max(0.35, 1.05-wave*0.06);
      }
      if (waveTimer > 18) {
        waveTimer = 0;
        wave++;
        updateHud();
      }
    }

    for (var bi=bullets.length-1; bi>=0; bi--) {
      bullets[bi].y -= bullets[bi].s*dt;
      if (bullets[bi].y < -20) bullets.splice(bi,1);
    }

    for (var ei=enemies.length-1; ei>=0; ei--) {
      var e = enemies[ei];
      e.t += dt;
      if (e.type === "zig") e.x += Math.sin(e.t*4)*100*dt;
      e.y += e.s*dt;

      if (e.y > H+40) {
        enemies.splice(ei,1);
        if (mode === "story") damage();
        continue;
      }
      if (overlap(player,e)) {
        enemies.splice(ei,1);
        damage();
      }
    }

    if (boss) {
      boss.t += dt;
      boss.x = W/2 + Math.sin(boss.t)*260;
      boss.y = 105 + Math.sin(boss.t*1.7)*18;
    }

    for (var b=bullets.length-1; b>=0; b--) {
      var shot = bullets[b];
      var used = false;

      for (var j=enemies.length-1; j>=0; j--) {
        if (rectCircle(enemies[j], shot)) {
          enemies[j].hp--;
          bullets.splice(b,1);
          used = true;
          if (enemies[j].hp <= 0) {
            score += enemies[j].type === "tank" ? 120 : (enemies[j].type === "zig" ? 80 : 50);
            enemies.splice(j,1);
            updateHud();
            storyProgress();
          }
          break;
        }
      }

      if (!used && boss && rectCircle(boss, shot)) {
        bullets.splice(b,1);
        boss.hp--;
        score += 10;
        updateHud();
        if (boss.hp <= 0) {
          boss = null;
          score += 1500;
          updateHud();
          victory();
        }
      }
    }
  }

  function drawBackground() {
    var g = ctx.createLinearGradient(0,0,0,H);
    g.addColorStop(0,"#06081d");
    g.addColorStop(0.55,"#120b35");
    g.addColorStop(1,"#21104b");
    ctx.fillStyle = g;
    ctx.fillRect(0,0,W,H);

    ctx.fillStyle = "#8660c7";
    ctx.globalAlpha = 0.55;
    ctx.beginPath();
    ctx.arc(W-120,115,70,0,Math.PI*2);
    ctx.fill();
    ctx.globalAlpha = 1;

    ctx.fillStyle = "#fff";
    for (var i=0;i<stars.length;i++) {
      ctx.beginPath();
      ctx.arc(stars[i].x,stars[i].y,stars[i].r,0,Math.PI*2);
      ctx.fill();
    }
  }

  function drawAccessory(name) {
    if (name === "Mono estelar") {
      ctx.fillStyle="#ff5fa9";
      ctx.fillRect(10,-28,16,12);
    } else if (name === "Casco espacial") {
      ctx.strokeStyle="#9ef3ff";
      ctx.lineWidth=4;
      ctx.beginPath();
      ctx.arc(0,-3,30,Math.PI*1.08,Math.PI*1.92);
      ctx.stroke();
    } else if (name === "Visor corazon") {
      ctx.fillStyle="#ff6fb4";
      ctx.font="16px sans-serif";
      ctx.textAlign="center";
      ctx.fillText("♥  ♥",0,0);
    } else if (name === "Corona lunar") {
      ctx.fillStyle="#ffe59d";
      ctx.beginPath();
      ctx.moveTo(-14,-25);ctx.lineTo(-8,-38);ctx.lineTo(0,-28);ctx.lineTo(8,-39);ctx.lineTo(15,-25);
      ctx.closePath();
      ctx.fill();
    }
  }

  function drawCat(x,y,scale) {
    var c=skins[skin];
    ctx.save();
    ctx.translate(x,y);
    ctx.scale(scale,scale);
    if (inv>0 && Math.floor(inv*12)%2===0) ctx.globalAlpha=0.35;

    ctx.fillStyle=c[1];
    ctx.beginPath();ctx.moveTo(-21,-13);ctx.lineTo(-12,-34);ctx.lineTo(-2,-14);ctx.closePath();ctx.fill();
    ctx.beginPath();ctx.moveTo(21,-13);ctx.lineTo(12,-34);ctx.lineTo(2,-14);ctx.closePath();ctx.fill();
    ctx.beginPath();ctx.ellipse(0,-3,27,24,0,0,Math.PI*2);ctx.fill();

    ctx.fillStyle=c[2];
    ctx.beginPath();ctx.ellipse(0,6,13,9,0,0,Math.PI*2);ctx.fill();

    ctx.fillStyle="#17142d";
    ctx.beginPath();ctx.arc(-9,-5,3,0,Math.PI*2);ctx.arc(9,-5,3,0,Math.PI*2);ctx.fill();

    ctx.fillStyle="#ff7faf";
    ctx.beginPath();ctx.arc(0,4,2.5,0,Math.PI*2);ctx.fill();

    drawAccessory(accessories[acc]);
    ctx.restore();
  }

  function drawRat(e) {
    ctx.save();
    ctx.translate(e.x,e.y);
    ctx.fillStyle="#f4ca65";
    ctx.beginPath();
    ctx.moveTo(-e.w/2,13);ctx.lineTo(e.w/2,7);ctx.lineTo(e.w/2-7,e.h/2);ctx.lineTo(-e.w/2+5,e.h/2);
    ctx.closePath();ctx.fill();

    ctx.fillStyle=e.type==="tank" ? "#817092" : "#a692b8";
    ctx.beginPath();ctx.ellipse(0,-5,e.type==="tank"?23:18,e.type==="tank"?18:15,0,0,Math.PI*2);ctx.fill();
    ctx.beginPath();ctx.arc(-13,-17,6,0,Math.PI*2);ctx.arc(13,-17,6,0,Math.PI*2);ctx.fill();

    ctx.fillStyle="#17142d";
    ctx.beginPath();ctx.arc(-6,-6,2,0,Math.PI*2);ctx.arc(6,-6,2,0,Math.PI*2);ctx.fill();
    ctx.restore();
  }

  function drawBoss() {
    if (!boss) return;
    ctx.save();
    ctx.translate(boss.x,boss.y);
    ctx.fillStyle="#6e4a98";
    ctx.beginPath();ctx.ellipse(0,18,75,40,0,0,Math.PI*2);ctx.fill();
    ctx.fillStyle="#ae95c9";
    ctx.beginPath();ctx.ellipse(0,-12,40,32,0,0,Math.PI*2);ctx.fill();
    ctx.fillStyle="#ffe59d";
    ctx.beginPath();ctx.moveTo(-25,-40);ctx.lineTo(-13,-60);ctx.lineTo(0,-45);ctx.lineTo(13,-62);ctx.lineTo(28,-40);ctx.closePath();ctx.fill();
    ctx.restore();
  }

  function render() {
    drawBackground();

    for (var i=0;i<enemies.length;i++) drawRat(enemies[i]);
    drawBoss();

    ctx.fillStyle="#d7fbff";
    for (var b=0;b<bullets.length;b++) {
      ctx.beginPath();
      ctx.arc(bullets[b].x,bullets[b].y,bullets[b].r,0,Math.PI*2);
      ctx.fill();
    }

    if (state === "play" || state === "story" || state === "over" || state === "win") {
      drawCat(player.x,player.y,1);
    } else {
      drawCat(W*0.35,H*0.7,1.1);
      drawCat(W*0.65,H*0.7,0.9);
    }
  }

  var toastTimer = null;
  function say(msg) {
    toast.textContent = msg;
    toast.classList.remove("gg-hidden");
    clearTimeout(toastTimer);
    toastTimer = setTimeout(function(){ toast.classList.add("gg-hidden"); }, 1800);
  }

  function loop(t) {
    var dt = Math.min(0.033, (t-last)/1000 || 0);
    last=t;
    update(dt);
    render();
    requestAnimationFrame(loop);
  }

  showMenu();
  requestAnimationFrame(loop);
})();
</script>

## Uso de Inteligencia Artificial

Se utilizó ChatGPT como apoyo para plantear la idea del videojuego, desarrollar la estructura en HTML, crear los estilos en CSS y programar el funcionamiento con JavaScript. También se utilizó para corregir errores y agregar el modo historia, la personalización del personaje, los enemigos y el jefe final.
