<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi Videojuego</title>
  <style>
    body {
      text-align: center;
      background: #111;
      color: white;
      font-family: Arial, sans-serif;
    }
    #playButton {
      cursor: pointer;
      margin-top: 50px;
      width: 200px;
    }
    #gameCanvas {
      display: none; /* oculto hasta que se presione play */
      margin-top: 20px;
      background: black;
      border: 2px solid white;
    }
  </style>
</head>
<body>

  <h1>🎮 Mi Videojuego</h1>
  <img src="images/play.png" id="playButton" alt="Botón Play">


  <canvas id="gameCanvas" width="400" height="400"></canvas>

  <script>
   
    const playButton = document.getElementById('playButton');
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');

    
    playButton.addEventListener('click', () => {
      playButton.style.display = "none";   // ocultar botón
      canvas.style.display = "block";      // mostrar el juego
      iniciarJuego();                      // arrancar el juego
    });

    function iniciarJuego() {
      let x = 200;
      let y = 200;
      let dx = 2;
      let dy = 2;
      let radio = 15;

      function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

     
        ctx.beginPath();
        ctx.arc(x, y, radio, 0, Math.PI * 2);
        ctx.fillStyle = "lime";
        ctx.fill();
        ctx.closePath();

        x += dx;
        y += dy;

    
        if (x + radio > canvas.width || x - radio < 0) dx *= -1;
        if (y + radio > canvas.height || y - radio < 0) dy *= -1;

        requestAnimationFrame(draw);
      }
