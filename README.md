# Analizador-de-productos-USfans
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Analizador de productos USFans</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Familjen+Grotesk:wght@400;600;700&display=swap">
<style>
:root{--bg:#eef2ef;--card:#fbfcfb;--ink:#13221e;--mute:#566660;--line:#cdd8d3;--acc:#0e5b4b;--acc-ink:#fff;--ok:#0e7a4f;--mid:#a86a00;--bad:#b3261e;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1815;--card:#17231f;--ink:#e8f0ec;--mute:#93a69e;--line:#2b3c36;--acc:#4fc3a1;--acc-ink:#06241b;--ok:#4fd49a;--mid:#e5a63b;--bad:#ff7b72;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0f1815;--card:#17231f;--ink:#e8f0ec;--mute:#93a69e;--line:#2b3c36;--acc:#4fc3a1;--acc-ink:#06241b;--ok:#4fd49a;--mid:#e5a63b;--bad:#ff7b72;color-scheme:dark}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font:400 16px/1.55 "Familjen Grotesk",system-ui,-apple-system,"Segoe UI",sans-serif}
main{max-width:720px;margin:0 auto;padding:28px 18px 60px}
h1{font-size:clamp(2rem,7vw,3rem);line-height:1.05;margin:0 0 10px;letter-spacing:-.02em}
.lead{color:var(--mute);margin:0 0 24px;max-width:56ch}
.f{margin-bottom:16px}
label.l{display:block;font-weight:600;margin-bottom:4px}
.h{font-size:.85rem;color:var(--mute);margin:0 0 6px}
input,select,textarea{width:100%;font:inherit;color:var(--ink);background:var(--card);border:1.5px solid var(--line);border-radius:10px;padding:11px 12px}
textarea{min-height:170px;resize:vertical}
.two{display:grid;grid-template-columns:1fr 1fr;gap:12px}
@media(max-width:520px){.two{grid-template-columns:1fr}}
:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.go{font:inherit;font-weight:700;background:var(--acc);color:var(--acc-ink);border:0;border-radius:10px;padding:14px 22px;cursor:pointer;width:100%;font-size:1.05rem}
.go:disabled{opacity:.5;cursor:not-allowed}
.res{margin-top:26px}
.oc{padding:20px;border-radius:12px;border:2px solid currentColor;background:var(--card)}
.oc p,.oc ul,.oc h3{color:var(--ink)}
.stamp{display:inline-block;font-weight:700;font-size:1.35rem;border:3px solid currentColor;border-radius:8px;padding:4px 12px;transform:rotate(-2deg);margin-bottom:12px}
.ok{color:var(--ok)}.mid{color:var(--mid)}.bad{color:var(--bad)}
.meter{height:12px;background:var(--line);border-radius:6px;overflow:hidden;margin:4px 0 14px}
.meter i{display:block;height:100%;background:currentColor}
.row{display:flex;justify-content:space-between;font-weight:600}
h3{font-size:1rem;margin:16px 0 4px}
ul{padding-left:20px;margin:4px 0}li{margin:3px 0}
.note{font-size:.85rem;color:var(--mute);margin-top:16px;border-top:1px solid var(--line);padding-top:12px}
.msg{padding:14px;border-radius:10px;background:var(--card);border:1px solid var(--line);color:var(--mute)}
.err{color:var(--bad)}
.hr{display:flex;gap:6px;margin-bottom:8px}
.hi{flex:1;text-align:left;font:inherit;color:var(--ink);background:var(--card);border:1.5px solid currentColor;border-radius:10px;padding:10px 12px;cursor:pointer}
.hi span{display:block;font-size:.8rem;color:var(--mute)}
.hi b{color:var(--ink)}
.hx{font:inherit;color:var(--mute);background:var(--card);border:1.5px solid var(--line);border-radius:10px;padding:0 14px;cursor:pointer}
.lnk{font:inherit;background:none;border:0;color:var(--mute);text-decoration:underline;cursor:pointer;padding:6px 0}
#hist h2{font-size:1.1rem;margin:32px 0 10px}
.hidden{display:none}
details{background:var(--card);border:1px solid var(--line);border-radius:10px;padding:12px 14px;margin-bottom:18px}
summary{font-weight:600;cursor:pointer}
details p,details li{font-size:.92rem;color:var(--mute)}
</style>
</head>
<body>
<main>
<h1>Analiza un producto de USFans</h1>
<p class="lead">Pega el link y copia aquí el texto de la página del producto (título, precio, descripción, reseñas). La IA lo revisa y te dice si parece original o réplica y qué calidad tiene.</p>

<details><summary>Guía de calidades de réplicas (G5, PK, etc.)</summary>
<p>Son nombres informales que usan vendedores y compradores, no estándares oficiales. Cambian con el tiempo y cada fábrica sube y baja de nivel, así que tómalos como referencia aproximada.</p>
<ul>
<li><b>Nivel alto:</b> PK (PK God) y LJR suelen considerarse lo mejor en zapatillas, con materiales y forma muy cercanos al original. Son también las más caras.</li>
<li><b>Nivel medio-alto:</b> G5, OG y H12 se consideran buenas en relación con su precio, con algunos detalles que se notan al compararlas con la original.</li>
<li><b>Nivel medio:</b> lotes como M y otras fábricas intermedias: buena apariencia, materiales y forma menos precisos.</li>
<li><b>Nivel bajo:</b> sin nombre de fábrica o con etiquetas como “A”, “AA” o “top quality”. Son imitaciones evidentes.</li>
<li><b>Términos de marketing:</b> “1:1”, “AAA”, “UA” o “mirror” no garantizan nada, cualquier vendedor los usa.</li>
</ul>
<p>Los nombres de lote se usan sobre todo en zapatillas. En otras categorías suelen venderse solo como “A, AA, AAA”.</p>
</details>

<form id="form" onsubmit="return false">
<div class="f"><label class="l" for="url">Link del producto</label>
<input id="url" type="url" inputmode="url" placeholder="https://www.usfans.com/product/..."></div>

<div class="f"><label class="l" for="cat">Tipo de producto</label>
<select id="cat"><option value="">Que lo detecte la IA</option><option>Zapatillas</option><option>Ropa</option><option>Audífonos o electrónica</option><option>Relojes</option><option>Bolsos y accesorios</option><option>Ventiladores y gadgets</option><option>Otro</option></select></div>

<div class="two">
<div class="f"><label class="l" for="p1">Precio en USFans</label><input id="p1" placeholder="Ej: 28 USD"></div>
<div class="f"><label class="l" for="p2">Precio oficial (si lo sabes)</label><input id="p2" placeholder="Ej: 150 USD"></div>
</div>

<div class="f"><label class="l" for="txt">Texto de la página del producto</label>
<p class="h">Abre el producto, selecciona todo (Ctrl+A en computador, o mantén presionado en el celular), copia y pega aquí. Mientras más detalle, mejor el análisis: título, descripción, vendedor, reseñas y comentarios de compradores.</p>
<textarea id="txt" placeholder="Pega aquí lo que copiaste..."></textarea></div>

<button class="go" id="go" disabled>Analizar producto</button>
<p class="h">Aviso de privacidad: el texto que pegues se envía a la IA de Google para analizarlo. Al ser el servicio gratuito, Google puede usarlo para mejorar sus productos. No pegues datos personales.</p>
</form>

<div class="res" id="res" aria-live="polite"></div>

<section id="hist" class="hidden"><h2>Historial de verificaciones</h2><div id="hl"></div><button class="lnk" id="clr" type="button">Borrar historial</button><p class="h">Se guarda solo en este navegador y este dispositivo. Si borras los datos del navegador, se pierde.</p></section>
</main>

<script>
var $=function(i){return document.getElementById(i)};
var go=$("go"),res=$("res"),ctl=null;
function ready(){go.disabled=$("txt").value.trim().length<20}
["txt","url"].forEach(function(i){$(i).addEventListener("input",ready)});
ready();

function E(t,c,txt){var e=document.createElement(t);if(c)e.className=c;if(txt!=null)e.textContent=txt;return e}
function list(title,arr){if(!arr||!arr.length)return null;var w=E("div");w.appendChild(E("h3",null,title));var u=E("ul");arr.forEach(function(x){u.appendChild(E("li",null,String(x)))});w.appendChild(u);return w}
function meter(label,val,cls){var w=E("div");var r=E("div","row");r.appendChild(E("span",null,label));r.appendChild(E("span",null,val+"%"));w.appendChild(r);var m=E("div","meter "+cls);var i=E("i");i.style.width=Math.max(0,Math.min(100,val))+"%";m.appendChild(i);w.appendChild(m);return w}
function clsOf(n,hi,lo){return n>=hi?"ok":n>=lo?"mid":"bad"}

function show(d){res.textContent="";
var a=+d.autenticidad||0,q=+d.calidad||0;
var v=String(d.veredicto||"").toLowerCase();
var cls=v==="original"?"ok":v==="dudoso"?"mid":"bad";
var tit=v==="original"?"Probablemente original":v==="dudoso"?"Dudoso":"Probable réplica";
var box=E("div","oc "+cls);
if(d.producto)box.appendChild(E("p",null,d.producto));
box.appendChild(E("div","stamp",tit));
if(d.resumen)box.appendChild(E("p",null,d.resumen));
box.appendChild(meter("Autenticidad",a,cls));
var ql=q>=75?"Calidad alta":q>=45?"Calidad media":"Calidad baja";
box.appendChild(meter(ql,q,clsOf(q,75,45)));
if(d.nivel_replica&&cls!=="ok")box.appendChild(E("p",null,"Nivel estimado: "+d.nivel_replica));
if(d.lote_replica&&cls!=="ok")box.appendChild(E("p",null,"Lote mencionado: "+d.lote_replica));
[list("Señales de alerta",d.senales_alerta),list("Señales positivas",d.senales_positivas),list("Qué verificar antes de comprar",d.que_verificar)].forEach(function(x){if(x)box.appendChild(x)});
if(d.recomendacion){box.appendChild(E("h3",null,"Recomendación"));box.appendChild(E("p",null,d.recomendacion))}
box.appendChild(E("p","note","Es una estimación basada solo en el texto que pegaste, sin ver el producto real. La confirmación definitiva es validar la serie con la marca o usar un servicio de autenticación."));
res.appendChild(box);box.scrollIntoView({behavior:"smooth"})}

go.onclick=async function(){
if(ctl)ctl.abort();ctl=new AbortController();
go.disabled=true;go.textContent="Analizando...";res.textContent="";
try{
var r=await fetch("/api/analyze",{method:"POST",headers:{"Content-Type":"application/json"},signal:ctl.signal,
body:JSON.stringify({url:$("url").value,cat:$("cat").value,p1:$("p1").value,p2:$("p2").value,txt:$("txt").value})});
var d=await r.json();if(!r.ok)throw new Error(d.error||"No se pudo analizar.");show(d);addH(d)}
catch(e){if(e.name!=="AbortError")res.appendChild(E("div","msg err",e.message||"No se pudo analizar. Inténtalo de nuevo."))}
go.textContent="Analizar producto";ready()};

var HK="historial_v1";
function getH(){try{return JSON.parse(localStorage.getItem(HK)||"[]")}catch(e){return[]}}
function setH(a){try{localStorage.setItem(HK,JSON.stringify(a.slice(0,50)))}catch(e){}}
function addH(d){var a=getH();a.unshift({f:new Date().toLocaleString("es"),u:$("url").value.slice(0,300),d:d});setH(a);renderH()}
function renderH(){var a=getH(),w=$("hl");w.textContent="";$("hist").classList.toggle("hidden",!a.length);
a.forEach(function(x,i){var v=String(x.d.veredicto||"").toLowerCase();
var cls=v==="original"?"ok":v==="dudoso"?"mid":"bad";
var tit=v==="original"?"Probablemente original":v==="dudoso"?"Dudoso":"Probable réplica";
var row=E("div","hr");var b=E("button","hi "+cls);b.type="button";
b.appendChild(E("b",null,(x.d.producto||"Producto")+" · "+tit));
b.appendChild(E("span",null,"Autenticidad "+(x.d.autenticidad||0)+"% · Calidad "+(x.d.calidad||0)+"% · "+x.f));
b.onclick=function(){if(x.u)$("url").value=x.u;show(x.d)};
var del=E("button","hx","✕");del.type="button";del.setAttribute("aria-label","Eliminar esta verificación");
del.onclick=function(){var h=getH();h.splice(i,1);setH(h);renderH()};
row.appendChild(b);row.appendChild(del);w.appendChild(row)})}
$("clr").onclick=function(){if(confirm("¿Borrar todo el historial?")){setH([]);renderH()}};
renderH();
</script>
</body>
</html>
