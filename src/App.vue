<template>
  <div class="container">
    <h1 class="titulo" @mouseenter="hover = true" @mouseleave="hover = false" @touchstart="hover = true"
      @touchend="hover = false" :class="{ active: hover }">
      📊 Reporte de Power BI 🚀
    </h1>
    <p class="subtitulo">
      ✨ Visualización interactiva de datos generada en Power BI 🔍
    </p>

    <div class="iframe-container">
      <iframe title="visualizacionDaatamartN" width="1140" height="541.25"
        src="https://app.powerbi.com/reportEmbed?reportId=f8b75f38-2df9-4c21-8233-a50db50b5aca&autoAuth=true&ctid=c2677f10-7216-4412-8262-de0b610ace4c"
        frameborder="0" allowFullScreen="true"></iframe>
        <br>
    </div>
<br>
    <div class="minesweeper-container">
      <h2>🎯 Juego de Buscaminas</h2>
      <div id="minesweeper"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hover: false,
    };
  },
  mounted() {
    this.initMinesweeper();
  },
  methods: {
    initMinesweeper() {
      const size = 8;
      const mines = 10;
      const grid = [];
      const container = document.getElementById("minesweeper");
      container.innerHTML = "";
      container.style.display = "grid";
      container.style.gridTemplateColumns = `repeat(${size}, 30px)`;
      container.style.gap = "4px";
      const minePositions = new Set();
      while (minePositions.size < mines) {
        minePositions.add(Math.floor(Math.random() * size * size));
      }

      for (let i = 0; i < size * size; i++) {
        const cell = document.createElement("div");
        cell.classList.add("cell");
        cell.dataset.index = i;
        cell.style.width = "30px";
        cell.style.height = "30px";
        cell.style.background = "#ddd";
        cell.style.display = "flex";
        cell.style.alignItems = "center";
        cell.style.justifyContent = "center";
        cell.style.cursor = "pointer";
        cell.style.fontWeight = "bold";
        grid.push(cell);
        container.appendChild(cell);
      }

      grid.forEach((cell, i) => {
        cell.addEventListener("click", () => {
          if (minePositions.has(i)) {
            cell.innerText = "💣";
            cell.style.background = "#f44336";
            alert("¡Boom! Perdiste.");
          } else {
            const nearby = countNearbyMines(i);
            cell.innerText = nearby || "";
            cell.style.background = "#a5d6a7";
            cell.style.pointerEvents = "none";
          }
        });
      });

      function countNearbyMines(index) {
        const neighbors = [
          -1, 1, -size, size, -size - 1, -size + 1, size - 1, size + 1,
        ];
        return neighbors.reduce((acc, offset) => {
          const nIndex = index + offset;
          if (
            nIndex >= 0 &&
            nIndex < size * size &&
            Math.abs((index % size) - (nIndex % size)) <= 1 &&
            minePositions.has(nIndex)
          ) {
            acc++;
          }
          return acc;
        }, 0);
      }
    },
  },
};
</script>
