<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Panel SkyUltraPlus</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #1e1e2f;
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .login-container, .panel-container {
      background: #29293d;
      padding: 30px;
      border-radius: 10px;
      display: none;
      flex-direction: column;
      gap: 15px;
      width: 300px;
      text-align: center;
    }
    input, button {
      padding: 10px;
      border: none;
      width: 100%;
      border-radius: 5px;
    }
    button {
      background: #61dafb;
      color: #000;
      font-weight: bold;
      cursor: pointer;
    }
    .visible {
      display: flex !important;
    }
    h2 {
      margin-top: 0;
    }
  </style>
</head>
<body>

  <div class="login-container visible" id="login">
    <h2>Iniciar Sesión</h2>
    <input type="text" id="usuario" placeholder="Usuario" required />
    <input type="password" id="password" placeholder="Contraseña" required />
    <button onclick="login()">Entrar</button>
    <p id="mensaje" style="color: red;"></p>
  </div>

  <div class="panel-container" id="panel">
    <h2>Bienvenido 👋</h2>
    <p id="saludo"></p>
    <button onclick="logout()">Cerrar sesión</button>
  </div>

  <script>
    const usuarios = {
      "admin": "admin123", // usuario: contraseña
      "demo": "demo2025"
    };

    function login() {
      const usuario = document.getElementById("usuario").value;
      const password = document.getElementById("password").value;
      const mensaje = document.getElementById("mensaje");

      if (usuarios[usuario] && usuarios[usuario] === password) {
        document.getElementById("login").classList.remove("visible");
        document.getElementById("panel").classList.add("visible");
        document.getElementById("saludo").textContent = `Hola, ${usuario}`;
      } else {
        mensaje.textContent = "❌ Usuario o contraseña incorrectos";
      }
    }

    function logout() {
      document.getElementById("login").classList.add("visible");
      document.getElementById("panel").classList.remove("visible");
      document.getElementById("usuario").value = "";
      document.getElementById("password").value = "";
      document.getElementById("mensaje").textContent = "";
    }
  </script>

</body>
</html>