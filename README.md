[![Play Button](inicio.png)](ruta-a-tu-juego-o-archivo)
    
        if (x + radio > canvas.width || x - radio < 0) dx *= -1;
        if (y + radio > canvas.height || y - radio < 0) dy *= -1;

        requestAnimationFrame(draw);
      }
