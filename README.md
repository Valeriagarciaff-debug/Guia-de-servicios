<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Guía de Servicios en Loreto</title>

<style>
:root{
    --azul:#2563eb;
    --azul2:#1e3a8a;
    --fondo:#f1f5f9;
    --texto:#1f2937;
}

/* MODO OSCURO */
.dark{
    --fondo:#0f172a;
    --texto:#f1f5f9;
}

/* GENERAL */
body{
    font-family:'Segoe UI',sans-serif;
    margin:0;
    background:var(--fondo);
    color:var(--texto);
    transition:0.3s;
}

/* HEADER */
header{
    background:linear-gradient(135deg,var(--azul),var(--azul2));
    color:white;
    text-align:center;
    padding:50px 20px;
}

/* NAV */
nav{
    display:flex;
    justify-content:center;
    flex-wrap:wrap;
    gap:10px;
    background:white;
    padding:10px;
}

nav a{
    text-decoration:none;
    color:var(--azul);
    font-weight:bold;
}

/* SECCIONES */
.section{
    max-width:900px;
    margin:auto;
    padding:20px;
}

/* TARJETAS */
.card{
    background:white;
    padding:15px;
    border-radius:15px;
    margin:10px 0;
    box-shadow:0 10px 20px rgba(0,0,0,0.1);
    animation:fade 0.5s ease;
}

@keyframes fade{
    from{opacity:0; transform:translateY(10px);}
    to{opacity:1;}
}

/* IMÁGENES */
.card img{
    width:100%;
    border-radius:10px;
    margin-bottom:10px;
}

/* BOTONES */
button{
    background:var(--azul);
    color:white;
    border:none;
    padding:10px;
    border-radius:20px;
    margin:5px;
    cursor:pointer;
}

/* INPUT */
input{
    width:100%;
    padding:10px;
    margin:5px 0;
    border-radius:10px;
    border:1px solid #ccc;
}

/* FORM */
form{
    background:white;
    padding:20px;
    border-radius:15px;
}

/* MAPA */
iframe{
    width:100%;
    height:250px;
    border-radius:15px;
    border:none;
}

/* BOTON MODO OSCURO */
.toggle{
    position:fixed;
    top:10px;
    right:10px;
}
</style>

</head>

<body>

<button class="toggle" onclick="modo()">🌙</button>

<header>
<h1>GUÍA DE SERVICIOS EN LORETO</h1>
<p>Encuentra servicios fácil y rápido</p>
</header>

<nav>
<a href="#servicios">Servicios</a>
<a href="#mapa">Mapa</a>
<a href="#registro">Registrar</a>
</nav>

<div class="section" id="servicios">
<h2>Servicios</h2>

<input type="text" placeholder="Buscar..." onkeyup="buscar(this.value)">

<div>
<button onclick="filtrar('carpintería')">🪵</button>
<button onclick="filtrar('viajes')">✈️</button>
<button onclick="filtrar('agua')">💧</button>
<button onclick="mostrar(negocios)">🔄</button>
</div>

<div id="lista"></div>
</div>

<div class="section" id="mapa">
<h2>Ubicación</h2>
<iframe src="https://maps.google.com/maps?q=Loreto%20Zacatecas&t=&z=13&ie=UTF8&iwloc=&output=embed"></iframe>
</div>

<div class="section" id="registro">
<h2>Registrar negocio</h2>

<form action="https://formsubmit.co/mivaleriagarcia@gmail.com" method="POST">
<input name="Nombre" placeholder="Nombre" required>
<input name="Tipo" placeholder="Tipo" required>
<input name="Dirección" placeholder="Dirección" required>
<input name="Teléfono" placeholder="Teléfono" required>

<button type="submit">Enviar</button>

<input type="hidden" name="_captcha" value="false">
</form>
</div>

<script>

let negocios=[
{nombre:"Carpintería Hernández",tipo:"carpintería",direccion:"Vega",telefono:"4961226521",img:"https://via.placeholder.com/400"},
{nombre:"Evelyn Viajes",tipo:"viajes",direccion:"Centro",telefono:"4492913218",img:"https://via.placeholder.com/400"},
{nombre:"Joel Trinidad",tipo:"agua",direccion:"Loreto",telefono:"4961278222",img:"https://via.placeholder.com/400"}
];

function mostrar(lista){
let html="";
lista.forEach(n=>{
html+=`
<div class="card">
<img src="${n.img}">
<h3>${n.nombre}</h3>
<p>${n.tipo}</p>
<p>${n.direccion}</p>
<p><a href="tel:${n.telefono}"> ${n.telefono}</a></p>
</div>`;
});
document.getElementById("lista").innerHTML=html;
}

function buscar(texto){
texto=texto.toLowerCase();
mostrar(negocios.filter(n=>n.tipo.includes(texto)));
}

function filtrar(tipo){
mostrar(negocios.filter(n=>n.tipo.includes(tipo)));
}

function modo(){
document.body.classList.toggle("dark");
}

mostrar(negocios);

</script>

</body>
</html>
