<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Escape Room Velora</title>
  <style>
    body {
      margin: 0;
      font-family: system-ui, sans-serif;
      background: #111111;
      color: #E2BC6F;
    }
    .container {
      max-width: 800px;
      margin: auto;
      padding: 20px;
      text-align: center;
    }
    h1, h2, h3 { color: #E2BC6F; }
    .card {
      background: rgba(255,255,255,0.05);
      border: 1px solid #E2BC6F;
      border-radius: 1rem;
      padding: 20px;
      margin-bottom: 20px;
      text-align: left;
    }
    input {
      width: 100%;
      padding: 10px;
      border-radius: 0.75rem;
      border: 1px solid #E2BC6F;
      background: #000;
      color: #E2BC6F;
      font-family: monospace;
      margin-top: 8px;
    }
    button {
      background: #E2BC6F;
      border: none;
      color: #111;
      padding: 10px 16px;
      border-radius: 0.75rem;
      cursor: pointer;
      margin-top: 10px;
      font-weight: bold;
    }
    button:hover { background: #d4a84d; }
    #timer {
      font-size: 1.2em;
      margin-bottom: 20px;
    }
    .hidden { display: none; }
    .success { border-color: #10b981; }
    img.logo {
      max-width: 160px;
      margin: 20px auto;
      display: block;
    }
  </style>
</head>
<body>
<div class="container">
  <img src="Velora_Isotipo_Blanco.png" alt="Velora" class="logo">
  <h1>🔐 Escape Room Velora</h1>
  <p>Bienvenido. Tienes 30 minutos para descubrir la nueva funcionalidad de Velora.</p>

  <div id="timer">⏱️ Tiempo: 30:00</div>

  <!-- Nivel 1 -->
  <div id="step1" class="card">
    <h2>1) Resuelve el acertijo matemático</h2>
    <p>
      Un número de 3 cifras.<br>
      • La suma de sus dígitos es 9.<br>
      • El dígito de las centenas es el doble del de las unidades.<br>
      • El dígito de las decenas es la mitad de las centenas.<br>
      ¿Cuál es el número?
    </p>
    <input id="input1" placeholder="Respuesta en números">
    <button onclick="check1()">Probar</button>
  </div>

  <!-- Nivel 2 -->
  <div id="step2" class="card hidden">
    <h2>2) Descifra el mensaje</h2>
    <p>Texto cifrado con César +3:</p>
    <pre>DLHQ</pre>
    <input id="input2" placeholder="Respuesta en mayúsculas">
    <button onclick="check2()">Probar</button>
  </div>

  <!-- Nivel 3 -->
  <div id="step3" class="card hidden">
    <h2>3) Une las piezas</h2>
    <p>Ordena los fragmentos para formar la palabra:</p>
    <pre>TE - CLI - EN - TO</pre>
    <input id="input3" placeholder="Respuesta en mayúsculas">
    <button onclick="check3()">Probar</button>
  </div>

  <!-- Nivel 4 -->
  <div id="step4" class="card hidden">
    <h2>4) La funcionalidad final</h2>
    <p>Has llegado al último reto. Escribe la palabra que representa la nueva funcionalidad de Velora.</p>
    <input id="input4" placeholder="Respuesta en mayúsculas">
    <button onclick="check4()">Probar</button>
  </div>

  <!-- Victoria -->
  <div id="win" class="card hidden">
    <h2>🎉 ¡Funcionalidad descubierta!</h2>
    <p>Has completado el escape room.</p>
    <p id="summary"></p>
    <p>Código de victoria: <code>VELORA-ONBOARDING-2026</code></p>
  </div>
</div>

<script>
  let seconds = 30*60;

  function updateTimer(){
    if (seconds > 0) seconds--;
    const m = String(Math.floor(seconds/60)).padStart(2,'0');
    const s = String(seconds%60).padStart(2,'0');
    document.getElementById('timer').textContent = `⏱️ Tiempo: ${m}:${s}`;
    if(seconds===0){ alert("Se acabó el tiempo"); }
  }
  setInterval(updateTimer,1000);

  function check1(){
    const val = document.getElementById('input1').value.trim();
    if(val==="234"){
      document.getElementById('step1').classList.add('hidden');
      document.getElementById('step2').classList.remove('hidden');
    } else {
      alert("No es correcto");
    }
  }
  function check2(){
    const val = document.getElementById('input2').value.trim().toUpperCase();
    if(val==="AI"){
      document.getElementById('step2').classList.add('hidden');
      document.getElementById('step3').classList.remove('hidden');
    } else {
      alert("No es correcto");
    }
  }
  function check3(){
    const val = document.getElementById('input3').value.trim().toUpperCase();
    if(val==="CLIENTE"){
      document.getElementById('step3').classList.add('hidden');
      document.getElementById('step4').classList.remove('hidden');
    } else {
      alert("No es correcto");
    }
  }
  function check4(){
    const val = document.getElementById('input4').value.trim().toUpperCase();
    if(val==="ONBOARDING"){
      document.getElementById('step4').classList.add('hidden');
      document.getElementById('win').classList.remove('hidden');
      const used = 30*60 - seconds;
      const m = Math.floor(used/60);
      const s = used%60;
      document.getElementById('summary').textContent = `Tiempo invertido: ${m}m ${s}s`;
    } else {
      alert("No es correcto");
    }
  }
</script>
</body>
</html>

