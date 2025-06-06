<script setup>

</script>

<template>
  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="css/Style.css">
    <title>Reportr de PowerBi</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      margin: 0;
      overflow: hidden;
    }

    #juego {
      position: relative;
      width: 100vw;
      height: 100vh;
    }

    #circulo {
      position: absolute;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background-color: red;
      cursor: pointer;
    }

    #contador {
      position: absolute;
      top: 10px;
      left: 10px;
      font-size: 24px;
      background: white;
      padding: 10px;
      border-radius: 8px;
      box-shadow: 0 0 10px #ccc;
    }
  </style>

</head>
<body>

    <div class="container">
        <h1>Reportr de PowerBi</h1>
        <p>Visualizacion interactiva de datos generar de Power BI</p>
        <div class="iframe-container">
          


          
  <div id="juego">
    <div id="contador">Puntos: 0</div>
    <div id="circulo"></div>
  </div>

  <script>
    const circulo = document.getElementById("circulo");
    const contador = document.getElementById("contador");
    let puntos = 0;

    function moverCirculo() {
      const maxX = window.innerWidth - 60;
      const maxY = window.innerHeight - 60;
      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      circulo.style.left = x + "px";
      circulo.style.top = y + "px";
    }

    circulo.addEventListener("click", () => {
      puntos++;
      contador.textContent = "Puntos: " + puntos;
      moverCirculo();
    });

    // Mover el círculo la primera vez
    moverCirculo();
  </script>




        </div>
    </div>
</body>
</html>
 
</template>

