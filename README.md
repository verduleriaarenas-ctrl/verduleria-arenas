<!DOCTYPE html>

<html lang="es">

<head>

<meta charset="utf-8">

<meta name="viewport" content="width=device-width, initial-scale=1">

<title>Arenas Frutas y Verduras · Hacé tu pedido</title>

<meta name="theme-color" content="#1d5a34">

<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@600;800\&family=Nunito:wght@400;700\&display=swap" rel="stylesheet">

<style>

:root{

&#x20; --verde:#1d5a34; --verde2:#2f8a4f; --hoja:#e6f2e3; --tomate:#d8432e; --sol:#f4b63d;

&#x20; --fondo:#f7faf5; --tarjeta:#ffffff; --texto:#1b2a20; --suave:#5d6f63; --linea:#d9e4d6;

&#x20; --sombra:0 2px 10px rgba(29,90,52,.10);

}

@media (prefers-color-scheme:dark){

&#x20; :root{--fondo:#121a15;--tarjeta:#1c2820;--texto:#eaf3ec;--suave:#a3b5a8;--linea:#2c3d32;--hoja:#223229;--verde:#7fd59a;--verde2:#4fb374;--sombra:none}

}

\*{box-sizing:border-box;margin:0}

html{scroll-padding-top:130px}

body{font-family:"Nunito",system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;background:var(--fondo);color:var(--texto);line-height:1.45;padding-bottom:96px}

h1,h2,h3,.titulo{font-family:"Baloo 2","Trebuchet MS",system-ui,sans-serif}

button,input,select,textarea{font:inherit;color:inherit}

button{cursor:pointer}

:focus-visible{outline:3px solid var(--sol);outline-offset:2px}



header{background:#1d5a34;color:#fff;padding:18px 16px 14px;text-align:center}

header h1{font-size:clamp(1.5rem,5vw,2.2rem);font-weight:800;line-height:1.1}

header p{opacity:.9;font-size:.95rem;margin-top:4px}

.pasos{display:flex;justify-content:center;gap:8px;flex-wrap:wrap;margin-top:10px;font-size:.85rem}

.pasos span{background:rgba(255,255,255,.15);padding:3px 10px;border-radius:99px}



.barra{position:sticky;top:0;z-index:20;background:var(--fondo);padding:10px 12px 8px;border-bottom:1px solid var(--linea)}

.barra-in{max-width:980px;margin:auto;display:grid;gap:8px}

.tabs{display:grid;grid-template-columns:1fr 1fr;gap:6px;background:var(--hoja);padding:4px;border-radius:14px}

.tab{border:0;background:transparent;padding:10px;border-radius:11px;font-weight:700;font-size:1.05rem}

.tab\[aria-selected=true]{background:var(--verde2);color:#fff}

.buscar{width:100%;padding:11px 14px;border:2px solid var(--linea);border-radius:12px;background:var(--tarjeta)}

.buscar:focus{border-color:var(--verde2);outline:none}



main{max-width:980px;margin:auto;padding:14px 12px}

.grilla{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:12px}

.prod{background:var(--tarjeta);border:2px solid var(--linea);border-radius:16px;padding:12px 10px;text-align:center;display:flex;flex-direction:column;gap:8px;box-shadow:var(--sombra);transition:border-color .15s}

.prod.activo{border-color:var(--verde2);background:var(--hoja)}

.emoji{font-size:2.6rem;line-height:1}

.nombre{font-weight:700;font-size:1.02rem;line-height:1.2;min-height:2.4em;display:flex;align-items:center;justify-content:center}

.unidad{display:flex;justify-content:center;gap:4px}

.unidad button{border:1.5px solid var(--linea);background:transparent;border-radius:99px;padding:2px 10px;font-size:.8rem;color:var(--suave)}

.unidad button\[aria-pressed=true]{background:var(--verde2);border-color:var(--verde2);color:#fff}

.cant{display:flex;align-items:center;justify-content:center;gap:8px}

.cant button{width:42px;height:42px;border-radius:50%;border:0;font-size:1.5rem;font-weight:800;background:var(--verde2);color:#fff;line-height:1}

.cant button.menos{background:var(--tarjeta);color:var(--tomate);border:2px solid var(--tomate)}

.cant button:disabled{opacity:.3}

.cant output{min-width:62px;font-weight:800;font-size:1.05rem}

.vacio{text-align:center;color:var(--suave);padding:40px 10px}



.otro{background:var(--tarjeta);border:2px dashed var(--linea);border-radius:16px;padding:12px;margin-top:14px}

.otro label{font-weight:700;display:block;margin-bottom:6px}

.otro textarea,.form textarea{width:100%;padding:10px 12px;border:2px solid var(--linea);border-radius:12px;background:var(--tarjeta);resize:vertical;min-height:60px}



.carrito{position:fixed;left:0;right:0;bottom:0;z-index:30;padding:10px 12px calc(10px + env(safe-area-inset-bottom,0px));background:linear-gradient(transparent,var(--fondo) 35%)}

.carrito button{display:flex;width:100%;max-width:560px;margin:auto;align-items:center;justify-content:space-between;gap:10px;border:0;border-radius:16px;padding:14px 18px;background:var(--tomate);color:#fff;font-weight:800;font-size:1.1rem;box-shadow:0 6px 18px rgba(216,67,46,.35)}

.carrito button:disabled{background:#8a968d;box-shadow:none}

.cuenta{background:#fff;color:var(--tomate);border-radius:99px;min-width:28px;padding:0 9px;text-align:center}



.fondo-modal{position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:40;display:none;align-items:flex-end;justify-content:center}

.fondo-modal.abierto{display:flex}

.hoja-pedido{background:var(--fondo);width:100%;max-width:620px;max-height:94vh;overflow:auto;border-radius:22px 22px 0 0;padding:16px 16px calc(20px + env(safe-area-inset-bottom,0px));animation:sube .22s ease-out}

@keyframes sube{from{transform:translateY(40px);opacity:0}to{transform:none;opacity:1}}

@media (prefers-reduced-motion:reduce){.hoja-pedido{animation:none}}

.cab{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}

.cab h2{font-size:1.4rem}

.cerrar{border:0;background:var(--hoja);width:38px;height:38px;border-radius:50%;font-size:1.2rem}

.lista{list-style:none;padding:0;border:1px solid var(--linea);border-radius:14px;background:var(--tarjeta);margin-bottom:14px}

.lista li{display:flex;align-items:center;gap:10px;padding:9px 12px;border-bottom:1px solid var(--linea)}

.lista li:last-child{border:0}

.lista .n{flex:1;font-weight:700}

.lista .q{color:var(--suave);white-space:nowrap}

.lista .x{border:0;background:transparent;color:var(--tomate);font-size:1.2rem;width:34px;height:34px}

.form{display:grid;gap:12px}

.campo label,.campo legend{font-weight:700;display:block;margin-bottom:4px;font-size:.95rem}

.campo input\[type=text],.campo input\[type=tel]{width:100%;padding:11px 12px;border:2px solid var(--linea);border-radius:12px;background:var(--tarjeta)}

.campo input:focus,textarea:focus{border-color:var(--verde2);outline:none}

.campo input.error{border-color:var(--tomate)}

.opciones{display:flex;flex-wrap:wrap;gap:8px;border:0;padding:0}

.opciones label{display:inline-flex;margin:0;font-weight:700}

.opciones input{position:absolute;opacity:0}

.opciones span{border:2px solid var(--linea);border-radius:99px;padding:8px 14px;background:var(--tarjeta)}

.opciones input:checked+span{background:var(--verde2);border-color:var(--verde2);color:#fff}

.opciones input:focus-visible+span{outline:3px solid var(--sol);outline-offset:2px}

.msg-error{color:var(--tomate);font-weight:700;font-size:.9rem;min-height:1.2em}

.enviar{border:0;border-radius:16px;padding:15px;background:#1faa59;color:#fff;font-weight:800;font-size:1.15rem;display:flex;justify-content:center;gap:10px;align-items:center}

.vaciar{border:0;background:transparent;color:var(--suave);text-decoration:underline;padding:8px}

.nota{font-size:.82rem;color:var(--suave);text-align:center}

footer{text-align:center;color:var(--suave);font-size:.85rem;padding:20px 12px}

</style>

</head>

<body>



<header>

&#x20; <h1>🥬 Arenas Frutas y Verduras</h1>

&#x20; <p>Armá tu pedido y lo recibimos por WhatsApp</p>

&#x20; <div class="pasos"><span>1 · Elegí</span><span>2 · Completá tus datos</span><span>3 · Enviá por WhatsApp</span></div>

</header>



<div class="barra">

&#x20; <div class="barra-in">

&#x20;   <div class="tabs" role="tablist" aria-label="Categorías">

&#x20;     <button class="tab" role="tab" id="tab-frutas" aria-selected="true" data-cat="frutas">🍎 Frutas</button>

&#x20;     <button class="tab" role="tab" id="tab-verduras" aria-selected="false" data-cat="verduras">🥕 Verduras</button>

&#x20;   </div>

&#x20;   <input class="buscar" id="buscar" type="search" placeholder="Buscar producto…" aria-label="Buscar producto">

&#x20; </div>

</div>



<main>

&#x20; <div class="grilla" id="grilla" role="tabpanel" aria-live="polite"></div>

&#x20; <div class="otro">

&#x20;   <label for="otro" id="otro-label">¿Otra fruta?</label>

&#x20;   <textarea id="otro" placeholder="Escribí acá lo que no encuentres. Ej: 2 kg de higos"></textarea>

&#x20; </div>

</main>



<footer>Reclamos dentro de las 24 hs · Arenas Frutas y Verduras</footer>



<div class="carrito">

&#x20; <button id="abrir" disabled><span>🧺 Ver mi pedido</span><span class="cuenta" id="cuenta">0</span></button>

</div>



<div class="fondo-modal" id="modal" role="dialog" aria-modal="true" aria-labelledby="t-modal">

&#x20; <div class="hoja-pedido">

&#x20;   <div class="cab"><h2 id="t-modal">Tu pedido</h2><button class="cerrar" id="cerrar" aria-label="Cerrar">✕</button></div>

&#x20;   <ul class="lista" id="lista"></ul>

&#x20;   <div class="form">

&#x20;     <div class="campo"><label for="nom">Nombre y apellido \*</label><input type="text" id="nom" autocomplete="name"></div>

&#x20;     <div class="campo"><label for="tel">Teléfono</label><input type="tel" id="tel" autocomplete="tel" inputmode="tel"></div>

&#x20;     <fieldset class="campo opciones" aria-label="Entrega">

&#x20;       <legend>¿Cómo lo recibís?</legend>

&#x20;       <label><input type="radio" name="ent" value="Envío a domicilio" checked><span>🛵 Envío</span></label>

&#x20;       <label><input type="radio" name="ent" value="Retiro en el local"><span>🏪 Retiro en el local</span></label>

&#x20;     </fieldset>

&#x20;     <div class="campo" id="box-dom"><label for="dom">Domicilio \*</label><input type="text" id="dom" autocomplete="street-address"></div>

&#x20;     <fieldset class="campo opciones" aria-label="Forma de pago">

&#x20;       <legend>Forma de pago</legend>

&#x20;       <label><input type="radio" name="pago" value="Efectivo" checked><span>💵 Efectivo</span></label>

&#x20;       <label><input type="radio" name="pago" value="Transferencia"><span>🏦 Transferencia</span></label>

&#x20;       <label><input type="radio" name="pago" value="Tarjeta"><span>💳 Tarjeta</span></label>

&#x20;       <label><input type="radio" name="pago" value="Cuenta corriente"><span>📒 Cta. cte.</span></label>

&#x20;     </fieldset>

&#x20;     <div class="campo"><label for="obs">Observaciones</label><textarea id="obs" placeholder="Ej: tomates bien maduros, horario de entrega…"></textarea></div>

&#x20;     <div class="msg-error" id="error" role="alert"></div>

&#x20;     <button class="enviar" id="enviar">Enviar pedido por WhatsApp</button>

&#x20;     <p class="nota">Se abrirá WhatsApp con tu pedido listo. Solo tenés que tocar “Enviar”.</p>

&#x20;     <button class="vaciar" id="vaciar">Vaciar pedido</button>

&#x20;   </div>

&#x20; </div>

</div>



<script>

/\* ===== CONFIGURACIÓN: cambiá este número por el WhatsApp del negocio =====

&#x20;  Formato internacional sin + ni espacios. Argentina: 549 + código de área + número.

&#x20;  Ejemplo: 5492946123456 \*/

const WHATSAPP = "5492940000000";

const NEGOCIO = "Arenas Frutas y Verduras";



/\* Productos tomados del talonario. u = unidad por defecto (kg | un | doc) \*/

const P = \[

&#x20;\["frutas","Banana","🍌","kg"],\["frutas","Banana (docena)","🍌","doc"],\["frutas","Manzana roja","🍎","kg"],

&#x20;\["frutas","Manzana verde","🍏","kg"],\["frutas","Naranja","🍊","kg"],\["frutas","Mandarina","🍊","kg"],

&#x20;\["frutas","Limón","🍋","kg"],\["frutas","Pomelo","🍊","kg"],\["frutas","Pera","🍐","kg"],

&#x20;\["frutas","Durazno","🍑","kg"],\["frutas","Ciruela","🍑","kg"],\["frutas","Uva","🍇","kg"],

&#x20;\["frutas","Frutilla","🍓","kg"],\["frutas","Sandía","🍉","kg"],\["frutas","Melón","🍈","kg"],

&#x20;\["frutas","Ananá","🍍","un"],\["frutas","Kiwi","🥝","kg"],\["frutas","Palta","🥑","un"],

&#x20;\["frutas","Arándanos","🫐","kg"],\["frutas","Cereza","🍒","kg"],\["frutas","Damasco","🍑","kg"],

&#x20;\["verduras","Papa","🥔","kg"],\["verduras","Batata","🍠","kg"],\["verduras","Cebolla","🧅","kg"],

&#x20;\["verduras","Cebolla de verdeo","🌱","un"],\["verduras","Zanahoria","🥕","kg"],\["verduras","Tomate","🍅","kg"],

&#x20;\["verduras","Tomate cherry","🍅","kg"],\["verduras","Lechuga","🥬","un"],\["verduras","Espinaca","🥬","un"],

&#x20;\["verduras","Acelga","🥬","un"],\["verduras","Zapallo anco","🎃","kg"],\["verduras","Zapallito","🥒","kg"],

&#x20;\["verduras","Zucchini","🥒","kg"],\["verduras","Morrón rojo","🫑","kg"],\["verduras","Morrón verde","🫑","kg"],

&#x20;\["verduras","Pepino","🥒","kg"],\["verduras","Berenjena","🍆","kg"],\["verduras","Choclo","🌽","un"],

&#x20;\["verduras","Ajo","🧄","kg"],\["verduras","Brócoli","🥦","un"],\["verduras","Coliflor","🥦","un"]

].map((\[c,n,e,u],i)=>({id:i,cat:c,nombre:n,emoji:e,u}));



const $ = s => document.querySelector(s);

let cat = "frutas", filtro = "";

let pedido = {};   // id -> {q, u}

try { pedido = JSON.parse(localStorage.getItem("pedido-arenas") || "{}"); } catch(e){}

const guardar = () => { try { localStorage.setItem("pedido-arenas", JSON.stringify(pedido)); } catch(e){} };



const paso = u => u === "kg" ? 0.5 : 1;

const etq = (q,u) => {

&#x20; const n = String(q).replace(".", ",");

&#x20; if (u === "kg") return `${n} kg`;

&#x20; if (u === "doc") return `${n} ${q===1?"docena":"docenas"}`;

&#x20; return `${n} ${q===1?"unidad":"unidades"}`;

};

const norm = s => s.toLowerCase().normalize("NFD").replace(/\[\\u0300-\\u036f]/g,"");



function dibujar(){

&#x20; const g = $("#grilla");

&#x20; const lista = P.filter(p => p.cat === cat \&\& norm(p.nombre).includes(norm(filtro)));

&#x20; g.innerHTML = lista.length ? "" : '<p class="vacio">No encontramos ese producto. Probá otra palabra o escribilo en “Otra” al final.</p>';

&#x20; lista.forEach(p => {

&#x20;   const it = pedido\[p.id];

&#x20;   const u = it ? it.u : p.u, q = it ? it.q : 0;

&#x20;   const d = document.createElement("div");

&#x20;   d.className = "prod" + (q ? " activo" : "");

&#x20;   d.innerHTML = `<div class="emoji" aria-hidden="true">${p.emoji}</div><div class="nombre">${p.nombre}</div>

&#x20;     <div class="unidad" role="group" aria-label="Unidad">

&#x20;       ${p.u==="doc" ? `<button aria-pressed="true" disabled>docena</button>` :

&#x20;         `<button data-u="kg" aria-pressed="${u==="kg"}">kg</button><button data-u="un" aria-pressed="${u==="un"}">unidad</button>`}

&#x20;     </div>

&#x20;     <div class="cant"><button class="menos" aria-label="Quitar ${p.nombre}" ${q?"":"disabled"}>−</button>

&#x20;     <output>${q ? etq(q,u) : "0"}</output><button class="mas" aria-label="Agregar ${p.nombre}">+</button></div>`;

&#x20;   d.querySelector(".mas").onclick = () => cambiar(p, 1);

&#x20;   d.querySelector(".menos").onclick = () => cambiar(p, -1);

&#x20;   d.querySelectorAll(".unidad \[data-u]").forEach(b => b.onclick = () => {

&#x20;     const nu = b.dataset.u, cur = pedido\[p.id];

&#x20;     if (cur) { cur.u = nu; if (nu !== "kg") cur.q = Math.max(1, Math.round(cur.q)); }

&#x20;     else pedido\[p.id] = {q: paso(nu), u: nu};

&#x20;     guardar(); dibujar(); actualizar();

&#x20;   });

&#x20;   g.appendChild(d);

&#x20; });

}



function cambiar(p, dir){

&#x20; const cur = pedido\[p.id] || {q:0, u:p.u};

&#x20; cur.q = Math.max(0, +(cur.q + dir\*paso(cur.u)).toFixed(1));

&#x20; if (cur.q === 0) delete pedido\[p.id]; else pedido\[p.id] = cur;

&#x20; guardar(); dibujar(); actualizar();

}



function actualizar(){

&#x20; const n = Object.keys(pedido).length;

&#x20; $("#cuenta").textContent = n;

&#x20; $("#abrir").disabled = n === 0 \&\& !$("#otro").value.trim();

&#x20; if (n === 0 \&\& $("#modal").classList.contains("abierto") \&\& !$("#otro").value.trim()) cerrar();

&#x20; else if ($("#modal").classList.contains("abierto")) dibujarLista();

}



function dibujarLista(){

&#x20; const ul = $("#lista"); ul.innerHTML = "";

&#x20; Object.entries(pedido).forEach((\[id,it]) => {

&#x20;   const p = P\[id], li = document.createElement("li");

&#x20;   li.innerHTML = `<span aria-hidden="true">${p.emoji}</span><span class="n">${p.nombre}</span><span class="q">${etq(it.q,it.u)}</span><button class="x" aria-label="Quitar ${p.nombre}">✕</button>`;

&#x20;   li.querySelector(".x").onclick = () => { delete pedido\[id]; guardar(); dibujar(); actualizar(); };

&#x20;   ul.appendChild(li);

&#x20; });

&#x20; const otro = $("#otro").value.trim();

&#x20; if (otro){ const li = document.createElement("li"); li.innerHTML = `<span aria-hidden="true">✏️</span><span class="n">Otros: ${otro.replace(/</g,"\&lt;")}</span>`; ul.appendChild(li); }

}



const abrir = () => { dibujarLista(); $("#modal").classList.add("abierto"); $("#nom").focus(); };

const cerrar = () => $("#modal").classList.remove("abierto");



document.querySelectorAll(".tab").forEach(t => t.onclick = () => {

&#x20; cat = t.dataset.cat;

&#x20; document.querySelectorAll(".tab").forEach(x => x.setAttribute("aria-selected", x === t));

&#x20; $("#otro-label").textContent = cat === "frutas" ? "¿Otra fruta?" : "¿Otra verdura?";

&#x20; dibujar();

});

$("#buscar").oninput = e => { filtro = e.target.value; dibujar(); };

$("#otro").oninput = actualizar;

$("#abrir").onclick = abrir;

$("#cerrar").onclick = cerrar;

$("#modal").onclick = e => { if (e.target.id === "modal") cerrar(); };

document.addEventListener("keydown", e => { if (e.key === "Escape") cerrar(); });

$("#vaciar").onclick = () => { if (confirm("¿Vaciar todo el pedido?")){ pedido = {}; $("#otro").value=""; guardar(); dibujar(); actualizar(); cerrar(); } };



document.querySelectorAll('input\[name=ent]').forEach(r => r.onchange = () => {

&#x20; $("#box-dom").style.display = document.querySelector('input\[name=ent]:checked').value.startsWith("Retiro") ? "none" : "";

});



$("#enviar").onclick = () => {

&#x20; const val = n => document.querySelector(`input\[name=${n}]:checked`).value;

&#x20; const nom = $("#nom").value.trim(), dom = $("#dom").value.trim(), ent = val("ent");

&#x20; \["#nom","#dom"].forEach(s => $(s).classList.remove("error"));

&#x20; $("#error").textContent = "";

&#x20; if (!nom){ $("#nom").classList.add("error"); $("#nom").focus(); $("#error").textContent = "Escribí tu nombre para continuar."; return; }

&#x20; if (ent.startsWith("Envío") \&\& !dom){ $("#dom").classList.add("error"); $("#dom").focus(); $("#error").textContent = "Escribí tu domicilio para el envío."; return; }



&#x20; const f = new Date().toLocaleDateString("es-AR");

&#x20; let t = `\*NOTA DE PEDIDO – ${NEGOCIO}\*\\n📅 ${f}\\n\\n👤 \*Cliente:\* ${nom}\\n`;

&#x20; if ($("#tel").value.trim()) t += `📞 \*Tel.:\* ${$("#tel").value.trim()}\\n`;

&#x20; t += `🚚 \*Entrega:\* ${ent}\\n`;

&#x20; if (ent.startsWith("Envío")) t += `📍 \*Domicilio:\* ${dom}\\n`;

&#x20; t += `💳 \*Pago:\* ${val("pago")}\\n\\n\*PEDIDO:\*\\n`;

&#x20; Object.entries(pedido).forEach((\[id,it]) => { t += `• ${P\[id].nombre}: ${etq(it.q,it.u)}\\n`; });

&#x20; const otro = $("#otro").value.trim();

&#x20; if (otro) t += `• Otros: ${otro}\\n`;

&#x20; if ($("#obs").value.trim()) t += `\\n📝 \*Observaciones:\* ${$("#obs").value.trim()}\\n`;

&#x20; t += `\\n¡Gracias!`;

&#x20; window.open(`https://wa.me/542946513933?text=${encodeURIComponent(t)}`, "\_blank");

};



dibujar(); actualizar();

</script>

</body>

</html>

