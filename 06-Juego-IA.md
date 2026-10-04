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
.gg-item{font-weight:800}
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
(function(){
const C=document.getElementById("gg-canvas"),X=C.getContext("2d"),W=C.width,H=C.height;
const overlay=document.getElementById("gg-overlay"),menu=document.getElementById("gg-menu"),custom=document.getElementById("gg-custom");
const kicker=document.getElementById("gg-kicker"),title=document.getElementById("gg-title"),txt=document.getElementById("gg-text"),hint=document.getElementById("gg-hint");
const hud=document.getElementById("gg-hud"),livesEl=document.getElementById("gg-lives"),scoreEl=document.getElementById("gg-score"),waveEl=document.getElementById("gg-wave");
const bossHud=document.getElementById("gg-boss-hud"),bossLife=document.getElementById("gg-boss-life"),toast=document.getElementById("gg-toast");
const keys=new Set();

const skins=[
 ["Rosa cósmico","#ff9fd2","#fff0f8"],
 ["Azul nebulosa","#80dfff","#e9fbff"],
 ["Lila lunar","#b9a7ff","#f1edff"],
 ["Naranja solar","#ffb36b","#fff0de"],
 ["Menta estelar","#7ee6c2","#ecfff8"],
 ["Café meteorito","#b98a6d","#f8e8dc"]
];
const accessories=["Moño estelar","Casco espacial","Visor corazón","Corona lunar","Sin accesorio"];

let skin=0,acc=0,state="menu",mode="story",choice=0,score=0,lives=3,wave=1,last=0,spawn=0,waveTime=0,inv=0,boss=null,storyStage=0,slide=0,slides=[];
const bullets=[],enemies=[],enemyBullets=[],particles=[];
const stars=Array.from({length:125},()=>({x:Math.random()*W,y:Math.random()*H,r:.4+Math.random()*1.6,s:8+Math.random()*20,a:.25+Math.random()*.7}));
const p={x:W/2,y:H-70,w:56,h:44,speed:325,cd:0};

const intro=[
 ["CAPÍTULO 1 · UNA SEÑAL EXTRAÑA","Algo se acerca a Miau-9","El planeta de los gatitos vivía tranquilo entre jardines de estrellas. Una noche aparecieron cientos de naves con forma de queso: las ratas habían llegado."],
 ["TRANSMISIÓN RATA","Venimos por lo que nos quitaron","Las ratas dicen que fueron rechazadas, exiliadas y obligadas a abandonar sus hogares. Aseguran que quieren recuperar un lugar en la galaxia."],
 ["MISIÓN","Defiende Miau-9","Muévete con WASD o las flechas y dispara con ESPACIO. Sobrevive a las oleadas y descubre qué hay detrás de la invasión."]
];
const middle=[
 ["ARCHIVO ANTIGUO","La historia estaba incompleta","Los registros muestran que fueron humanos quienes expulsaron a las ratas de sus antiguas colonias y tomaron sus recursos. Miau-9 nunca participó en aquella guerra."],
 ["ALERTA","El Almirante Rattus se acerca","Los gatitos ofrecen diálogo, pero las tropas rata continúan atacando. Su nave principal acaba de entrar en órbita."]
];
const reveal=[
 ["JEFE FINAL · ALMIRANTE RATTUS","La verdadera razón","Rattus confiesa: los humanos sí les quitaron sus territorios, pero ahora invaden otros mundos porque les gusta conquistar y controlar nuevos planetas."],
 ["ÚLTIMA MISIÓN","Rompe el ciclo","Una injusticia pasada no justifica repetirla contra otros. Derrota a Rattus y protege Miau-9."]
];

const opts=[
 ["Modo historia",()=>startStory()],
 ["Modo libre",()=>startGame("free")],
 ["Personalizar gatito",()=>openCustom()],
 ["Controles",()=>showControls()]
];

function key(e){return e.code==="Space"?" ":e.key}
function insideGame(){return document.activeElement===C || C.matches(":hover")}
addEventListener("keydown",e=>{
 const k=key(e);
 if(!insideGame() && state==="play")return;
 if(["ArrowUp","ArrowDown","ArrowLeft","ArrowRight","w","a","s","d","W","A","S","D"," "].includes(k))e.preventDefault();
 keys.add(k.toLowerCase());
 if(e.repeat&&state!=="play")return;
 if(state==="menu")menuKey(k);
 else if(state==="custom")customKey(k);
 else if(state==="slide"&&k===" ")nextSlide();
 else if((state==="over"||state==="win")&&k===" ")showMenu();
});
addEventListener("keyup",e=>keys.delete(key(e).toLowerCase()));
C.tabIndex=0;
C.addEventListener("click",()=>C.focus());

function showMenu(){
 state="menu";choice=0;overlay.classList.remove("gg-hidden");hud.classList.add("gg-hidden");
 custom.classList.add("gg-hidden");menu.classList.remove("gg-hidden");
 kicker.textContent="PLANETA MIAU-9";title.textContent="Gatitos Galácticos";
 txt.textContent="Shooter kawaii de gatitos espaciales contra una invasión de ratas. Haz clic en el juego y usa el teclado.";
 hint.textContent="W/S o ↑/↓ para elegir · ESPACIO para aceptar";
 renderMenu();
}
function renderMenu(){
 menu.innerHTML="";
 opts.forEach((o,i)=>{const d=document.createElement("div");d.className="gg-item"+(i===choice?" gg-selected":"");d.textContent=o[0];menu.appendChild(d)});
}
function menuKey(k){
 if(k==="ArrowUp"||k==="w"||k==="W"){choice=(choice+opts.length-1)%opts.length;renderMenu()}
 if(k==="ArrowDown"||k==="s"||k==="S"){choice=(choice+1)%opts.length;renderMenu()}
 if(k===" ")opts[choice][1]();
}
function openCustom(){
 state="custom";menu.classList.add("gg-hidden");custom.classList.remove("gg-hidden");
 kicker.textContent="TALLER DE MODA ESPACIAL";title.textContent="Personaliza tu gatito";
 txt.textContent="Escoge el pelaje y un accesorio.";
 hint.textContent="A/D o ←/→: pelaje · W/S o ↑/↓: accesorio · ESPACIO: guardar";
 renderCustom();
}
function renderCustom(){
 custom.innerHTML='<div class="gg-row"><b>Pelaje</b><span>'+skins[skin][0]+'</span></div><div class="gg-row"><b>Accesorio</b><span>'+accessories[acc]+'</span></div><div class="gg-row"><b>Vista previa</b><span>🐱 ✦ 🚀</span></div>';
}
function customKey(k){
 if(k==="ArrowLeft"||k==="a"||k==="A"){skin=(skin+skins.length-1)%skins.length;renderCustom()}
 if(k==="ArrowRight"||k==="d"||k==="D"){skin=(skin+1)%skins.length;renderCustom()}
 if(k==="ArrowUp"||k==="w"||k==="W"){acc=(acc+accessories.length-1)%accessories.length;renderCustom()}
 if(k==="ArrowDown"||k==="s"||k==="S"){acc=(acc+1)%accessories.length;renderCustom()}
 if(k===" ")showMenu();
}
function showControls(){
 state="slide";menu.classList.add("gg-hidden");custom.classList.add("gg-hidden");
 kicker.textContent="CONTROLES";title.textContent="Solo teclado";
 txt.innerHTML="<b>WASD o flechas</b>: mover al gatito.<br><b>ESPACIO</b>: disparar y aceptar opciones.";
 hint.textContent="ESPACIO para volver";slides=[];slide=-1;
}
function startStory(){mode="story";storyStage=0;showSlides(intro)}
function showSlides(s){slides=s;slide=0;state="slide";overlay.classList.remove("gg-hidden");hud.classList.add("gg-hidden");menu.classList.add("gg-hidden");custom.classList.add("gg-hidden");renderSlide()}
function renderSlide(){const s=slides[slide];kicker.textContent=s[0];title.textContent=s[1];txt.textContent=s[2];hint.textContent="ESPACIO para continuar"}
function nextSlide(){
 if(slide===-1){showMenu();return}
 slide++;
 if(slide<slides.length){renderSlide();return}
 if(mode==="story"&&storyStage===0){storyStage=1;startGame("story")}
 else if(mode==="story"&&storyStage===2){storyStage=3;resume(false)}
 else if(mode==="story"&&storyStage===4){storyStage=5;resume(true)}
 else showMenu();
}
function reset(){bullets.length=0;enemies.length=0;enemyBullets.length=0;particles.length=0;boss=null}
function startGame(m){
 mode=m;reset();score=0;lives=3;wave=1;spawn=0;waveTime=0;inv=0;p.x=W/2;p.y=H-70;p.cd=0;
 state="play";overlay.classList.add("gg-hidden");hud.classList.remove("gg-hidden");bossHud.classList.add("gg-hidden");updateHud();C.focus();
 if(m==="free")say("Modo libre: resiste todo lo que puedas ✦",2000);
}
function resume(makeBoss){state="play";overlay.classList.add("gg-hidden");hud.classList.remove("gg-hidden");C.focus();if(makeBoss)makeBossFn()}
function updateHud(){
 livesEl.textContent=lives;scoreEl.textContent=score;waveEl.textContent=wave;
 if(boss){bossHud.classList.remove("gg-hidden");bossLife.style.width=Math.max(0,boss.hp/boss.max*100)+"%"}else bossHud.classList.add("gg-hidden");
}
function makeBossFn(){enemies.length=0;enemyBullets.length=0;boss={x:W/2,y:105,w:160,h:108,hp:65,max:65,t:0,cd:0};updateHud();say("JEFE FINAL: Almirante Rattus",2200)}
function spawnRat(){
 let type="normal",r=Math.random();
 if(wave>=3&&r>.8)type="tank";else if(wave>=2&&r>.58)type="zig";
 let e={x:60+Math.random()*(W-120),y:-45,w:44,h:36,hp:1,s:76+wave*9+Math.random()*22,t:Math.random()*8,type};
 if(type==="tank"){e.w=62;e.h=46;e.hp=3;e.s*=.72}
 if(type==="zig")e.hp=2;
 enemies.push(e);
}
function shoot(){bullets.push({x:p.x,y:p.y-30,r:5,s:540});p.cd=.18}
function enemyShot(x,y,vx,vy){enemyBullets.push({x,y,vx,vy,r:6})}
function hit(r,c){const x=Math.max(r.x-r.w/2,Math.min(c.x,r.x+r.w/2)),y=Math.max(r.y-r.h/2,Math.min(c.y,r.y+r.h/2)),dx=c.x-x,dy=c.y-y;return dx*dx+dy*dy<c.r*c.r}
function overlap(a,b){return Math.abs(a.x-b.x)<(a.w+b.w)/2&&Math.abs(a.y-b.y)<(a.h+b.h)/2}
function burst(x,y,c,n){for(let i=0;i<n;i++){let a=Math.random()*Math.PI*2,s=40+Math.random()*140;particles.push({x,y,vx:Math.cos(a)*s,vy:Math.sin(a)*s,life:.4+Math.random()*.4,max:.8,r:2+Math.random()*3,c})}}
function damage(){if(inv>0||state!=="play")return;lives--;inv=1.2;burst(p.x,p.y,"#ff9fd2",18);updateHud();if(lives<=0)gameOver()}
function gameOver(){state="over";overlay.classList.remove("gg-hidden");hud.classList.add("gg-hidden");menu.classList.add("gg-hidden");kicker.textContent="MISIÓN FALLIDA";title.textContent="Game Over";txt.textContent="Puntaje final: "+score+". Las ratas siguen en órbita, pero los gatitos volverán a intentarlo.";hint.textContent="ESPACIO para volver al menú"}
function win(){state="win";overlay.classList.remove("gg-hidden");hud.classList.add("gg-hidden");kicker.textContent="MIAU-9 ESTÁ A SALVO";title.textContent="Victoria galáctica ✦";txt.textContent="Derrotaste al Almirante Rattus con "+score+" puntos. Los gatitos detuvieron la invasión.";hint.textContent="ESPACIO para volver al menú"}
function storyCheck(){
 if(mode!=="story")return;
 if(storyStage===1&&score>=500){storyStage=2;showSlides(middle)}
 else if(storyStage===3&&score>=1100){storyStage=4;showSlides(reveal)}
}
function update(dt){
 stars.forEach(s=>{s.y+=s.s*dt;if(s.y>H){s.y=-3;s.x=Math.random()*W}});
 if(state!=="play")return;
 inv=Math.max(0,inv-dt);p.cd=Math.max(0,p.cd-dt);waveTime+=dt;
 let mx=0,my=0;
 if(keys.has("a")||keys.has("arrowleft"))mx--;
 if(keys.has("d")||keys.has("arrowright"))mx++;
 if(keys.has("w")||keys.has("arrowup"))my--;
 if(keys.has("s")||keys.has("arrowdown"))my++;
 if(mx&&my){mx*=.707;my*=.707}
 p.x+=mx*p.speed*dt;p.y+=my*p.speed*dt;
 p.x=Math.max(36,Math.min(W-36,p.x));p.y=Math.max(H*.43,Math.min(H-38,p.y));
 if(keys.has(" ")&&p.cd<=0)shoot();

 if(!boss){
   spawn-=dt;
   if(spawn<=0){spawnRat();spawn=Math.max(.28,1.03-wave*.07)}
   if(waveTime>18){waveTime=0;wave++;say("Oleada "+wave,1000);updateHud()}
 }
 bullets.forEach(b=>b.y-=b.s*dt);
 for(let i=bullets.length-1;i>=0;i--)if(bullets[i].y<-20)bullets.splice(i,1);

 for(let i=enemies.length-1;i>=0;i--){
   let e=enemies[i];e.t+=dt;
   if(e.type==="zig")e.x+=Math.sin(e.t*4.2)*108*dt;
   e.y+=e.s*dt;
   if(e.y>H+55){enemies.splice(i,1);if(mode==="story")damage();continue}
   if(overlap(p,e)){enemies.splice(i,1);damage();continue}
   if(Math.random()<.003*(1+wave*.12)){
     let dx=p.x-e.x,dy=p.y-e.y,m=Math.hypot(dx,dy)||1;
     enemyShot(e.x,e.y+16,dx/m*90,dy/m*150);
   }
 }
 if(boss){
   boss.t+=dt;boss.cd-=dt;
   boss.x=W/2+Math.sin(boss.t*.9)*280;
   boss.y=108+Math.sin(boss.t*1.6)*20;
   if(boss.cd<=0){
     for(let a=-2;a<=2;a++){let ang=Math.PI/2+a*.2;enemyShot(boss.x,boss.y+40,Math.cos(ang)*160,Math.sin(ang)*190)}
     boss.cd=1.05;
   }
 }
 for(let i=enemyBullets.length-1;i>=0;i--){
   let b=enemyBullets[i];b.x+=b.vx*dt;b.y+=b.vy*dt;
   if(b.x<-30||b.x>W+30||b.y>H+30){enemyBullets.splice(i,1);continue}
   if(hit(p,b)){enemyBullets.splice(i,1);damage()}
 }
 for(let bi=bullets.length-1;bi>=0;bi--){
   let b=bullets[bi],used=false;
   for(let ei=enemies.length-1;ei>=0;ei--){
     let e=enemies[ei];
     if(hit(e,b)){
       bullets.splice(bi,1);e.hp--;used=true;burst(b.x,b.y,"#9ef3ff",6);
       if(e.hp<=0){
         score+=e.type==="tank"?120:e.type==="zig"?80:50;
         burst(e.x,e.y,"#ffb3d9",16);enemies.splice(ei,1);updateHud();storyCheck();
       }
       break;
     }
   }
   if(used)continue;
   if(boss&&hit(boss,b)){
     bullets.splice(bi,1);boss.hp--;score+=10;burst(b.x,b.y,"#ffd0e8",7);updateHud();
     if(boss.hp<=0){burst(boss.x,boss.y,"#ff9fd2",70);boss=null;score+=2000;updateHud();win();return}
   }
 }
 for(let i=particles.length-1;i>=0;i--){let q=particles[i];q.x+=q.vx*dt;q.y+=q.vy*dt;q.life-=dt;if(q.life<=0)particles.splice(i,1)}
}
function background(){
 let g=X.createLinearGradient(0,0,0,H);g.addColorStop(0,"#06081d");g.addColorStop(.55,"#120b35");g.addColorStop(1,"#21104b");
 X.fillStyle=g;X.fillRect(0,0,W,H);
 X.globalAlpha=.7;X.fillStyle="#8658c7";X.beginPath();X.arc(W-125,125,75,0,Math.PI*2);X.fill();X.globalAlpha=1;
 stars.forEach(s=>{X.globalAlpha=s.a;X.fillStyle="#fff";X.beginPath();X.arc(s.x,s.y,s.r,0,Math.PI*2);X.fill()});X.globalAlpha=1;
}
function cat(x,y,sc){
 let c=skins[skin];X.save();X.translate(x,y);X.scale(sc,sc);if(inv>0&&Math.floor(inv*12)%2===0)X.globalAlpha=.35;
 X.fillStyle=c[1];
 X.beginPath();X.moveTo(-21,-13);X.lineTo(-12,-34);X.lineTo(-2,-14);X.closePath();X.fill();
 X.beginPath();X.moveTo(21,-13);X.lineTo(12,-34);X.lineTo(2,-14);X.closePath();X.fill();
 X.beginPath();X.ellipse(0,-3,27,24,0,0,Math.PI*2);X.fill();
 X.fillStyle=c[2];X.beginPath();X.ellipse(0,6,13,9,0,0,Math.PI*2);X.fill();
 X.fillStyle="#17142d";X.beginPath();X.arc(-9,-5,3,0,Math.PI*2);X.arc(9,-5,3,0,Math.PI*2);X.fill();
 X.fillStyle="#ff7faf";X.beginPath();X.arc(0,4,2.3,0,Math.PI*2);X.fill();
 accessory(accessories[acc]);
 X.fillStyle="#b9a7ff";X.fillRect(-35,13,12,10);X.fillRect(23,13,12,10);
 X.restore();
}
function accessory(a){
 if(a==="Moño estelar"){X.fillStyle="#ff5fa9";X.fillRect(10,-28,16,14);X.fillStyle="#ffe59d";X.beginPath();X.arc(17,-21,4,0,Math.PI*2);X.fill()}
 else if(a==="Casco espacial"){X.strokeStyle="#9ef3ff";X.lineWidth=4;X.beginPath();X.arc(0,-4,31,Math.PI*1.08,Math.PI*1.92);X.stroke()}
 else if(a==="Visor corazón"){X.fillStyle="#ff6fb4";X.font="18px sans-serif";X.textAlign="center";X.fillText("♥  ♥",0,0)}
 else if(a==="Corona lunar"){X.fillStyle="#ffe59d";X.beginPath();X.moveTo(-14,-25);X.lineTo(-8,-38);X.lineTo(0,-28);X.lineTo(8,-39);X.lineTo(15,-25);X.closePath();X.fill()}
}
function rat(e){
 X.save();X.translate(e.x,e.y);
 X.fillStyle="#f4ca65";X.beginPath();X.moveTo(-e.w/2,14);X.lineTo(e.w/2,7);X.lineTo(e.w/2-8,e.h/2);X.lineTo(-e.w/2+6,e.h/2);X.closePath();X.fill();
 X.fillStyle=e.type==="tank"?"#8c7aa8":"#a692b8";X.beginPath();X.ellipse(0,-5,e.type==="tank"?24:18,e.type==="tank"?19:15,0,0,Math.PI*2);X.fill();
 X.beginPath();X.arc(-13,-17,6,0,Math.PI*2);X.arc(13,-17,6,0,Math.PI*2);X.fill();
 X.fillStyle="#17142d";X.beginPath();X.arc(-6,-6,2.3,0,Math.PI*2);X.arc(6,-6,2.3,0,Math.PI*2);X.fill();
 X.restore();
}
function drawBoss(){
 if(!boss)return;X.save();X.translate(boss.x,boss.y);
 X.fillStyle="#6e4a98";X.beginPath();X.ellipse(0,20,78,42,0,0,Math.PI*2);X.fill();
 X.fillStyle="#ae95c9";X.beginPath();X.ellipse(0,-12,42,34,0,0,Math.PI*2);X.fill();
 X.fillStyle="#ffe59d";X.beginPath();X.moveTo(-26,-42);X.lineTo(-14,-62);X.lineTo(0,-46);X.lineTo(14,-64);X.lineTo(29,-42);X.closePath();X.fill();
 X.fillStyle="#17142d";X.beginPath();X.arc(-14,-15,5,0,Math.PI*2);X.arc(14,-15,5,0,Math.PI*2);X.fill();
 X.restore();
}
function render(){
 background();enemies.forEach(rat);drawBoss();
 bullets.forEach(b=>{X.fillStyle="#d7fbff";X.beginPath();X.arc(b.x,b.y,b.r,0,Math.PI*2);X.fill()});
 enemyBullets.forEach(b=>{X.fillStyle="#ff92c3";X.beginPath();X.arc(b.x,b.y,b.r,0,Math.PI*2);X.fill()});
 particles.forEach(q=>{X.globalAlpha=Math.max(0,q.life/q.max);X.fillStyle=q.c;X.beginPath();X.arc(q.x,q.y,q.r,0,Math.PI*2);X.fill()});X.globalAlpha=1;
 if(state==="play"||state==="slide"||state==="over"||state==="win")cat(p.x,p.y,1);
 else{cat(W*.33,H*.68,1.15);cat(W*.67,H*.69,.9)}
}
let toastTimer;
function say(s,ms){toast.textContent=s;toast.classList.remove("gg-hidden");clearTimeout(toastTimer);toastTimer=setTimeout(()=>toast.classList.add("gg-hidden"),ms)}
function loop(t){let dt=Math.min(.033,(t-last)/1000||0);last=t;update(dt);render();requestAnimationFrame(loop)}
showMenu();requestAnimationFrame(loop);
})();
</script>

## Uso de Inteligencia Artificial

Se utilizó ChatGPT como apoyo para plantear la idea del videojuego, desarrollar la estructura en HTML, crear los estilos en CSS y programar el funcionamiento con JavaScript. También se utilizó para corregir errores y agregar el modo historia, la personalización del personaje, los enemigos y el jefe final.
