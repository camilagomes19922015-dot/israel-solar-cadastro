# israel-solar-cadastro
Cadastro
<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Cadastro Promoção – Israel Solar + D.Energy</title>
<style>
  :root {
    --azul:#1f4e79; 
    --amarelo:#ffcc33; 
    --bg:#f6f8fb;
  }
  * { box-sizing:border-box; }
  body {
    margin:0; font-family:Arial, Helvetica, sans-serif; background:var(--bg); color:#122;
  }
  header {
    background:white; padding:16px; border-bottom:4px solid var(--azul);
    display:flex; align-items:center; gap:16px; justify-content:center;
  }
  header img { height:72px; width:auto; }
  header .brand { display:flex; flex-direction:column; align-items:flex-start; }
  header .brand h1 { margin:0; font-size:22px; color:var(--azul); }
  header .brand small { color:#456; }
  main { max-width:760px; margin:24px auto; padding:16px; }
  .card { background:white; border-radius:14px; box-shadow:0 8px 24px rgba(0,0,0,.08); padding:20px; }
  h2 { margin:0 0 12px 0; color:var(--azul); }
  p.lead { margin-top:0; color:#345; }
  form { display:grid; gap:14px; margin-top:8px; }
  label { font-weight:600; color:#234; }
  input { padding:14px 12px; border:1px solid #ccd6e0; border-radius:10px; font-size:16px; }
  .actions { display:flex; gap:12px; flex-wrap:wrap; margin-top:8px; }
  button {
    appearance:none; border:none; background:var(--azul); color:white; padding:12px 16px;
    border-radius:10px; font-size:15px; font-weight:700; cursor:pointer;
  }
  .note { font-size:13px; color:#456; margin-top:10px; }
  footer { text-align:center; font-size:12px; color:#567; margin:24px 0; }
  .ig-list a { color:var(--azul); font-weight:700; text-decoration:none; }
  .success { display:none; }
  .success.active { display:block; }
  .success .cta { display:flex; gap:12px; flex-wrap:wrap; margin-top:12px; }
</style>
</head>
<body>
<header>
  <div class="brand">
    <h1>Cadastro Promoção – Israel Solar + D.Energy</h1>
    <small>Para validar sua inscrição, siga: 
      <span class="ig-list">
        <a href="https://www.instagram.com/placasolar.israel" target="_blank">@placasolar.israel</a> &nbsp;|&nbsp; 
        <a href="https://www.instagram.com/d.energysolar" target="_blank">@d.energysolar</a>
      </span>
    </small>
  </div>
</header>

<main>
  <div class="card">
    <div class="form-wrap">
      <h2>Preencha seus dados</h2>
      <p class="lead">Usaremos apenas para confirmar sua participação e contatar sobre os prêmios.</p>
      <form id="promoForm" onsubmit="return false;">
        <label>Nome completo
          <input id="nome" type="text" placeholder="Seu nome" required>
        </label>
        <label>Telefone / WhatsApp
          <input id="fone" type="tel" placeholder="(65) 99339-6331" required>
        </label>
        <div class="actions">
          <button onclick="enviarWhatsApp()">Enviar pelo WhatsApp</button>
        </div>
        <div class="note">Após enviar, você será encaminhado para seguir os perfis no Instagram.</div>
      </form>
    </div>

    <div id="success" class="success">
      <h2>Inscrição iniciada! 🎉</h2>
      <p class="lead">Terminando o envio, siga os perfis abaixo para validar sua participação:</p>
      <div class="cta">
        <a class="btn" target="_blank" href="https://www.instagram.com/placasolar.israel">Seguir @placasolar.israel</a>
        <a class="btn" style="background:var(--amarelo); color:#111;" target="_blank" href="https://www.instagram.com/d.energysolar">Seguir @d.energysolar</a>
      </div>
      <p class="note">Se os apps não abrirem automaticamente, toque nos botões acima.</p>
    </div>
  </div>

  <footer>
    © Israel Solar • Energia solar, o jeito certo de economizar!
  </footer>
</main>

<script>
function showSuccess() {
  document.querySelector('.form-wrap').style.display = 'none';
  document.getElementById('success').classList.add('active');
}

// Número oficial Israel Solar
const PHONE = "5565993396331"; 
const IG1 = "https://www.instagram.com/placasolar.israel";
const IG2 = "https://www.instagram.com/d.energysolar";

function dados() {
  const nome = document.getElementById('nome').value;
  const fone = document.getElementById('fone').value;
  return {nome, fone};
}

function validar() {
  const {nome, fone} = dados();
  if (!nome || !fone) { alert("Preencha todos os campos."); return false; }
  return true;
}

function abrirInstagramSequencia() {
  setTimeout(() => window.open(IG1, '_blank'), 400);
  setTimeout(() => window.open(IG2, '_blank'), 900);
}

function enviarWhatsApp() {
  if (!validar()) return;
  const d = dados();
  const texto = 
`Cadastro Promoção

Nome: ${d.nome}
Telefone: ${d.fone}
Confirmo que vou seguir @placasolar.israel e @d.energysolar.`;
  const msg = encodeURIComponent(texto);
  const url = `https://wa.me/${PHONE}?text=${msg}`;
  window.open(url, '_blank');
  showSuccess();
  abrirInstagramSequencia();
}
</script>
</body>
</html>
