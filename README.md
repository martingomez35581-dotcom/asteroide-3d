from pathlib import Path
import zipfile

root = Path("/mnt/data/actividad_asteroide_3d")
(root / "assets").mkdir(parents=True, exist_ok=True)

html = r'''<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Asteroide 3D: diseños personalizados e ideas convertidas en objetos mediante impresión 3D.">
  <meta name="theme-color" content="#30205d">
  <title>Asteroide 3D | Tus ideas toman forma</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header class="header">
    <a class="logo" href="#inicio"><span class="planet">✦</span> ASTEROIDE <b>3D</b></a>
    <nav aria-label="Navegación principal">
      <a href="#nosotros">Nosotros</a><a href="#productos">Diseños</a><a href="#proceso">Proceso</a><a href="#contacto">Contáctanos</a>
    </nav>
  </header>

  <main>
    <section class="hero" id="inicio">
      <div class="hero-text">
        <p class="eyebrow">IMAGINA · DISEÑA · CREA</p>
        <h1>Tus ideas<br>toman <span>forma.</span></h1>
        <p>En Asteroide 3D convertimos ideas en diseños personalizados mediante impresión 3D. Tú imaginas; nosotros te ayudamos a darles forma.</p>
        <a class="btn" href="#contacto">Cuéntanos tu idea <span>→</span></a>
        <p class="small">Diseños creativos para coleccionar, regalar y utilizar.</p>
      </div>
      <div class="hero-visual" role="img" aria-label="Ilustración decorativa de un objeto tridimensional y un planeta">
        <div class="orbit orbit-one"></div><div class="orbit orbit-two"></div>
        <div class="planet-big"><span>A3D</span></div>
        <div class="cube"><i></i><b></b><em></em></div>
        <span class="star star-one">✦</span><span class="star star-two">✧</span><span class="star star-three">✦</span>
        <div class="floating-tag">DISEÑO<br>PERSONALIZADO</div>
      </div>
    </section>

    <section class="section about" id="nosotros">
      <p class="eyebrow">CONOCE ASTEROIDE 3D</p>
      <h2>Más que figuras,<br><span>creamos ideas.</span></h2>
      <p class="lead">Asteroide 3D es una marca enfocada en crear productos personalizados a partir de las ideas de nuestros clientes. Buscamos ofrecer diseños creativos que puedan convertirse en figuras coleccionables o en objetos útiles para la vida cotidiana.</p>
      <div class="values">
        <article><span>✧</span><h3>Creatividad</h3><p>Escuchamos las ideas y buscamos convertirlas en propuestas originales.</p></article>
        <article><span>◇</span><h3>Personalización</h3><p>Cada propuesta parte de lo que el cliente imagina y necesita.</p></article>
        <article><span>◎</span><h3>Innovación</h3><p>Aprovechamos la impresión 3D para explorar nuevas posibilidades.</p></article>
      </div>
    </section>

    <section class="products" id="productos">
      <div class="section">
        <p class="eyebrow">NUESTROS DISEÑOS</p>
        <h2>Una idea puede convertirse<br>en muchas cosas.</h2>
        <p class="lead">Estos son ejemplos de las categorías que se pueden desarrollar. El diseño final depende de la idea y los requerimientos del cliente.</p>
        <div class="product-grid">
          <article class="product-card"><div class="product-art art-figure"><div class="mini-figure"><span></span></div></div><h3>Figuras coleccionables</h3><p>Personajes y objetos para quienes disfrutan coleccionar.</p></article>
          <article class="product-card"><div class="product-art art-useful"><div class="holder"><span></span></div></div><h3>Objetos funcionales</h3><p>Accesorios y piezas que pueden facilitar actividades cotidianas.</p></article>
          <article class="product-card"><div class="product-art art-custom"><div class="custom-shape">3D</div></div><h3>Diseños personalizados</h3><p>Propuestas creadas a partir de las ideas de cada cliente.</p></article>
        </div>
      </div>
    </section>

    <section class="section process" id="proceso">
      <p class="eyebrow">¿CÓMO LO HACEMOS?</p>
      <h2>De tu imaginación<br>al producto.</h2>
      <div class="steps">
        <article><b>01</b><div><h3>Nos cuentas tu idea</h3><p>El cliente explica qué quiere crear y para qué lo necesita.</p></div></article>
        <article><b>02</b><div><h3>Diseñamos la propuesta</h3><p>Se define el diseño y se revisan sus características.</p></div></article>
        <article><b>03</b><div><h3>Preparamos la impresión</h3><p>Se revisa el modelo digital y se prepara para la impresión 3D.</p></div></article>
        <article><b>04</b><div><h3>Hacemos realidad la idea</h3><p>Se realiza la impresión y se verifica el resultado final.</p></div></article>
      </div>
    </section>

    <section class="contact" id="contacto">
      <div>
        <p class="eyebrow">EMPIEZA A CREAR</p>
        <h2>¿Qué tienes<br>en mente?</h2>
        <p>Déjanos una idea de ejemplo. Este formulario es una demostración académica y no envía los datos a Asteroide 3D.</p>
      </div>
      <form id="idea-form">
        <label for="client">Tu nombre</label><input id="client" name="client" maxlength="40" placeholder="Escribe tu nombre" required>
        <label for="idea">Cuéntanos tu idea</label><textarea id="idea" name="idea" maxlength="250" placeholder="Quisiera un diseño de..." required></textarea>
        <button class="btn" type="submit">Enviar idea de prueba →</button>
        <small>La información solo se muestra en esta página; no se almacena.</small>
      </form>
      <div class="confirmation" id="confirmation" aria-live="polite" hidden></div>
    </section>
  </main>

  <footer>
    <a class="logo" href="#inicio">✦ ASTEROIDE <b>3D</b></a>
    <p>Convertimos ideas en diseños.</p>
    <small>Proyecto académico · Integración de contenidos digitales</small>
  </footer>
  <script src="script.js"></script>
</body>
</html>
'''

css = r'''*{box-sizing:border-box}
:root{--navy:#21183f;--purple:#6545a6;--violet:#a88be8;--pale:#f3efff;--blue:#dfeaff;--ink:#211d2e}
html{scroll-behavior:smooth}
body{margin:0;font-family:Arial,Helvetica,sans-serif;color:var(--ink);line-height:1.6}
.header{padding:18px 7%;display:flex;align-items:center;justify-content:space-between;gap:20px;background:#fff;border-bottom:1px solid #eee}
.logo{font-weight:900;letter-spacing:1.5px;color:var(--navy);text-decoration:none}.logo b{color:var(--purple)}.planet{color:var(--purple);font-size:1.5rem}
nav{display:flex;gap:22px;flex-wrap:wrap}nav a{color:var(--ink);text-decoration:none;font-size:.93rem}nav a:hover{color:var(--purple)}
.hero{padding:70px 9%;min-height:590px;display:grid;grid-template-columns:1fr 1fr;align-items:center;gap:35px;background:linear-gradient(120deg,#fff 45%,#f0ebff)}
.eyebrow{font-size:.76rem;letter-spacing:2px;color:var(--purple);font-weight:900}
h1{font-size:clamp(3.2rem,6vw,5.6rem);line-height:.98;letter-spacing:-3px;margin:15px 0 25px;color:var(--navy)}h1 span,h2 span{color:var(--purple)}
.hero-text>p:not(.eyebrow):not(.small){font-size:1.08rem;color:#5d586b;max-width:520px}
.btn{display:inline-block;background:var(--purple);color:white;border:0;border-radius:30px;padding:14px 23px;text-decoration:none;font-weight:800;cursor:pointer;font-size:.95rem}.btn:hover{background:var(--navy)}
.small{font-size:.82rem;color:#777;margin-top:17px}
.hero-visual{height:390px;position:relative;display:flex;align-items:center;justify-content:center;overflow:hidden}
.planet-big{height:230px;width:230px;border-radius:50%;background:radial-gradient(circle at 30% 25%,#c6b3ff,#7959c0 58%,#3b286f);box-shadow:inset -20px -20px 35px #21183f55,0 25px 45px #47327633;display:grid;place-items:center;color:#fff;font-size:2.2rem;font-weight:900;z-index:1}
.orbit{position:absolute;border:2px solid #a88be899;border-radius:50%;width:360px;height:125px;transform:rotate(-25deg)}.orbit-two{transform:rotate(48deg);width:320px;height:105px;border-color:#7597d788}
.cube{position:absolute;width:82px;height:82px;background:#8c6bc9;transform:rotate(-30deg) skew(8deg);right:9%;top:18%;box-shadow:12px 12px 0 #543b8a}.cube:before{content:"";position:absolute;inset:0;background:#b59be9;clip-path:polygon(0 0,50% 25%,100% 0,50% 0)}.cube:after{content:"";position:absolute;inset:0;background:#6d4da9;clip-path:polygon(0 0,50% 25%,50% 100%,0 75%)}.cube i{position:absolute;inset:0;background:#9b7bd6;clip-path:polygon(50% 25%,100% 0,100% 75%,50% 100%)}
.floating-tag{position:absolute;bottom:35px;right:12%;background:white;padding:12px 18px;border-radius:10px;color:var(--purple);font-weight:900;font-size:.75rem;letter-spacing:1px;box-shadow:0 8px 25px #24174418}
.star{position:absolute;color:var(--purple);font-size:2rem}.star-one{top:30px;left:20%}.star-two{bottom:60px;left:12%}.star-three{top:90px;right:12%}
.section{padding:80px 9%}.section h2,.contact h2{font-size:clamp(2.1rem,4vw,3.3rem);line-height:1.12;margin:8px 0 18px;color:var(--navy)}
.lead{max-width:760px;color:#625d70;font-size:1.05rem}
.values{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:38px}.values article{padding:25px;border-radius:16px;background:var(--pale)}.values article>span{font-size:2rem;color:var(--purple)}.values h3{margin:8px 0}.values p,.product-card p{color:#666;margin:0}
.products{background:#f7f5fc}.product-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;margin-top:35px}.product-card{background:white;border-radius:17px;padding:15px 15px 23px;box-shadow:0 8px 25px #271d4310}.product-card h3{margin:16px 8px 5px}.product-card p{margin:0 8px;font-size:.93rem}
.product-art{height:190px;border-radius:12px;background:linear-gradient(135deg,#e9e1ff,#dfeaff);display:grid;place-items:center;overflow:hidden}
.mini-figure{height:100px;width:76px;background:linear-gradient(90deg,#503783,#9474cf);border-radius:20px 20px 14px 14px;position:relative;box-shadow:10px 10px 0 #49327633}.mini-figure:before{content:"";position:absolute;width:72px;height:66px;border-radius:18px;background:#a78be0;top:-46px;left:2px}.mini-figure:after{content:"";position:absolute;width:14px;height:14px;background:#fff;border-radius:50%;top:-22px;left:16px;box-shadow:28px 0 #fff}.holder{width:105px;height:75px;border:12px solid #6e56a6;border-radius:12px 12px 25px 25px;position:relative;background:#fff}.holder:before{content:"";position:absolute;width:28px;height:45px;border:8px solid #9a80d1;border-bottom:0;top:-58px;left:16px;border-radius:15px 15px 0 0}.custom-shape{width:112px;height:112px;border-radius:28px;background:linear-gradient(135deg,#a78be0,#503783);display:grid;place-items:center;color:white;font-size:2rem;font-weight:900;transform:rotate(12deg);box-shadow:12px 12px 0 #50378333}
.steps{max-width:760px;margin-top:35px;display:grid;gap:15px}.steps article{display:flex;gap:22px;align-items:flex-start;padding:18px 22px;border:1px solid #e8e2f4;border-radius:14px}.steps article>b{font-size:1.35rem;color:var(--purple)}.steps h3{margin:0 0 4px}.steps p{margin:0;color:#686273}
.contact{background:var(--navy);color:white;padding:75px 9%;display:grid;grid-template-columns:1fr 1fr;gap:30px;align-items:center}.contact .eyebrow{color:#c6b4ff}.contact h2{color:white}.contact p{color:#ddd5f0;max-width:480px}
form{background:#fff;color:var(--ink);padding:26px;border-radius:17px;display:flex;flex-direction:column;gap:9px}label{font-weight:700;font-size:.9rem}input,textarea{font:inherit;padding:12px;border:1px solid #ddd;border-radius:8px;width:100%}textarea{min-height:100px;resize:vertical}form .btn{align-self:flex-start}form small{color:#777}.confirmation{grid-column:1/-1;background:#eee8ff;color:var(--navy);padding:18px;border-radius:12px;font-weight:700}
footer{padding:26px 9%;display:flex;justify-content:space-between;align-items:center;gap:15px;flex-wrap:wrap;background:#171329;color:#eee}footer .logo{color:#fff}footer p{margin:0}footer small{color:#c8c2d7}
@media(max-width:720px){.header{align-items:flex-start;flex-direction:column}nav{gap:13px}.hero{grid-template-columns:1fr;padding:55px 7%}.hero-visual{height:320px}.section{padding:60px 7%}.values,.product-grid{grid-template-columns:1fr}.contact{grid-template-columns:1fr;padding:60px 7%}.cube{right:5%}h1{letter-spacing:-1.5px}}
'''

js = r'''const form = document.querySelector("#idea-form");
const confirmation = document.querySelector("#confirmation");
form.addEventListener("submit", (event) => {
  event.preventDefault();
  const client = document.querySelector("#client").value.trim();
  const idea = document.querySelector("#idea").value.trim();
  if (!client || !idea) return;
  confirmation.textContent = ¡Gracias, ${client}! Tu idea de ejemplo quedó registrada en esta demostración: “${idea}”. Recuerda: este formulario no envía información real.;
  confirmation.hidden = false;
  confirmation.scrollIntoView({ behavior: "smooth", block: "center" });
});
'''

readme = '''# Asteroide 3D — estrategia digital

Sitio web académico para presentar Asteroide 3D, una marca que desarrolla diseños personalizados a partir de las ideas de sus clientes mediante impresión 3D.
