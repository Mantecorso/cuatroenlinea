<template>
  <div id="app">
    <div class="headerGrid">
      <div>
        <a href="https://vuejs.org" target="_blank"><img src="./assets/logo.png" class="logo"></a>
      </div>
      <div>
        <h1>Juego del cuatro en linea</h1>
      </div>
      <div>
        <a href="https://mantecorso.github.io/LuisJuradoQ/" target="_blank"><img src="./assets/L.png" class="logo" alt=""></a>
      </div>
    </div>

    <div class="row">
      <div class="col-12 espace">

        <table align="center" border="1">
          <tr>
            <td class="casilla" id="c0" v-on:click="pcelda(0)"></td>
            <td class="casilla" id="c1" v-on:click="pcelda(1)"></td>
            <td class="casilla" id="c2" v-on:click="pcelda(2)"></td>
            <td class="casilla" id="c3" v-on:click="pcelda(3)"></td>
            <td class="casilla" id="c4" v-on:click="pcelda(4)"></td>
            <td class="casilla" id="c5" v-on:click="pcelda(5)"></td>
            <td class="casilla" id="c6" v-on:click="pcelda(6)"></td>
          </tr>
          <tr>
            <td class="casilla" id="c7" v-on:click="pcelda(7)"></td>
            <td class="casilla" id="c8" v-on:click="pcelda(8)"></td>
            <td class="casilla" id="c9" v-on:click="pcelda(9)"></td>
            <td class="casilla" id="c10" v-on:click="pcelda(10)"></td>
            <td class="casilla" id="c11" v-on:click="pcelda(11)"></td>
            <td class="casilla" id="c12" v-on:click="pcelda(12)"></td>
            <td class="casilla" id="c13" v-on:click="pcelda(13)"></td>
          </tr>
          <tr>
            <td class="casilla" id="c14" v-on:click="pcelda(14)"></td>
            <td class="casilla" id="c15" v-on:click="pcelda(15)"></td>
            <td class="casilla" id="c16" v-on:click="pcelda(16)"></td>
            <td class="casilla" id="c17" v-on:click="pcelda(17)"></td>
            <td class="casilla" id="c18" v-on:click="pcelda(18)"></td>
            <td class="casilla" id="c19" v-on:click="pcelda(19)"></td>
            <td class="casilla" id="c20" v-on:click="pcelda(20)"></td>
          </tr>
          <tr>
            <td class="casilla" id="c21" v-on:click="pcelda(21)"></td>
            <td class="casilla" id="c22" v-on:click="pcelda(22)"></td>
            <td class="casilla" id="c23" v-on:click="pcelda(23)"></td>
            <td class="casilla" id="c24" v-on:click="pcelda(24)"></td>
            <td class="casilla" id="c25" v-on:click="pcelda(25)"></td>
            <td class="casilla" id="c26" v-on:click="pcelda(26)"></td>
            <td class="casilla" id="c27" v-on:click="pcelda(27)"></td>
          </tr>
          <tr>
            <td class="casilla" id="c28" v-on:click="pcelda(28)"></td>
            <td class="casilla" id="c29" v-on:click="pcelda(29)"></td>
            <td class="casilla" id="c30" v-on:click="pcelda(30)"></td>
            <td class="casilla" id="c31" v-on:click="pcelda(31)"></td>
            <td class="casilla" id="c32" v-on:click="pcelda(32)"></td>
            <td class="casilla" id="c33" v-on:click="pcelda(33)"></td>
            <td class="casilla" id="c34" v-on:click="pcelda(34)"></td>
          </tr>
          <tr>
            <td class="casilla" id="c35" v-on:click="pcelda(35)"></td>
            <td class="casilla" id="c36" v-on:click="pcelda(36)"></td>
            <td class="casilla" id="c37" v-on:click="pcelda(37)"></td>
            <td class="casilla" id="c38" v-on:click="pcelda(38)"></td>
            <td class="casilla" id="c39" v-on:click="pcelda(39)"></td>
            <td class="casilla" id="c40" v-on:click="pcelda(40)"></td>
            <td class="casilla" id="c41" v-on:click="pcelda(41)"></td>
          </tr>
        </table>
      </div>
      <div class="col-12 espace">

        <a href="javascript:location.reload()">
          <button type="button" class="btn btn-warning">Reiniciar</button></a>

      </div>

    </div>
  </div>
</template>

<script>
 export default {
    name: 'app',
    data: () => ({
      mapa: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ],
      jugador: 1,
    }),
    methods: {
      dibujar: function () {
        var i;
        for (i = 0; i < 42; i++) {
          if (this.mapa[i] == 0) {
            document.getElementById("c" + i).style = "background-color: palegreen";
          }
          if (this.mapa[i] == 1) {
            document.getElementById("c" + i).innerHTML = "X";
          }
          if (this.mapa[i] == 2) {
            document.getElementById("c" + i).innerHTML = "O";
          }
        }
      },
      pcelda: function (celda) {
        if (this.mapa[celda] == 0) {
          if (this.jugador == 1) {
            this.mapa[celda] = 1;
            this.jugador = 2;
          } else {
            this.mapa[celda] = 2;
            this.jugador = 1;
          }
        } else {
          alert("No puedes pulsar sobre una celda ya seleccionada por otro jugador");
        }
        this.dibujar();
        var r = this.ganador();
        switch (r) {
          case 0:
            break;
          case 1:
            alert("¡Ganó el jugador X!");
            break;
          case 2:
            alert("¡Ganó el jugador O!");
            break;
          case 3:
            alert("¡Empate!");
            break;
        }
      },
      ganador: function () {
        var numEspacios = 0;
        var i;
        for (i = 0; i < 42; i++) {
          if (this.mapa[i] == 0) numEspacios++;
        }
        // Las líneas horizontales
        //primera fila
        if (this.mapa[0] == this.mapa[1] && this.mapa[1] == this.mapa[2] && this.mapa[2] == this.mapa[3] && this.mapa[0] != 0) return this.mapa[0];
        if (this.mapa[1] == this.mapa[2] && this.mapa[2] == this.mapa[3] && this.mapa[3] == this.mapa[4] != 0) return this.mapa[1];
        if (this.mapa[2] == this.mapa[3] && this.mapa[3] == this.mapa[4] && this.mapa[4] == this.mapa[5] != 0) return this.mapa[2];
        if (this.mapa[3] == this.mapa[4] && this.mapa[4] == this.mapa[5] && this.mapa[5] == this.mapa[6] != 0) return this.mapa[3];
        // segunda fila
        if (this.mapa[7] == this.mapa[8] && this.mapa[8] == this.mapa[9] && this.mapa[9] == this.mapa[10] && this.mapa[7] != 0) return this.mapa[7];
        if (this.mapa[8] == this.mapa[9] && this.mapa[9] == this.mapa[10] && this.mapa[10] == this.mapa[11] && this.mapa[8] != 0) return this.mapa[8];
        if (this.mapa[9] == this.mapa[10] && this.mapa[10] == this.mapa[11] && this.mapa[11] == this.mapa[12] && this.mapa[9] != 0) return this.mapa[9];
        if (this.mapa[10] == this.mapa[11] && this.mapa[11] == this.mapa[12] && this.mapa[12] == this.mapa[13] && this.mapa[10] != 0) return this.mapa[10];
        // tercera fila
        if (this.mapa[14] == this.mapa[15] && this.mapa[15] == this.mapa[16] && this.mapa[16] == this.mapa[17] && this.mapa[14] != 0) return this.mapa[14];
        if (this.mapa[15] == this.mapa[16] && this.mapa[16] == this.mapa[17] && this.mapa[17] == this.mapa[18] && this.mapa[15] != 0) return this.mapa[15];
        if (this.mapa[16] == this.mapa[17] && this.mapa[17] == this.mapa[18] && this.mapa[18] == this.mapa[19] && this.mapa[16] != 0) return this.mapa[16];
        if (this.mapa[17] == this.mapa[18] && this.mapa[18] == this.mapa[19] && this.mapa[19] == this.mapa[20] && this.mapa[17] != 0) return this.mapa[17];
        //cuarta fila
        if (this.mapa[21] == this.mapa[22] && this.mapa[22] == this.mapa[23] && this.mapa[23] == this.mapa[24] && this.mapa[21] != 0) return this.mapa[21];
        if (this.mapa[22] == this.mapa[23] && this.mapa[23] == this.mapa[24] && this.mapa[24] == this.mapa[25] && this.mapa[22] != 0) return this.mapa[22];
        if (this.mapa[23] == this.mapa[24] && this.mapa[24] == this.mapa[25] && this.mapa[25] == this.mapa[26] && this.mapa[23] != 0) return this.mapa[23];
        if (this.mapa[24] == this.mapa[25] && this.mapa[25] == this.mapa[26] && this.mapa[26] == this.mapa[27] && this.mapa[24] != 0) return this.mapa[24];
        // quinta fila
        if (this.mapa[28] == this.mapa[29] && this.mapa[29] == this.mapa[30] && this.mapa[30] == this.mapa[31] && this.mapa[28] != 0) return this.mapa[28];
        if (this.mapa[29] == this.mapa[30] && this.mapa[30] == this.mapa[31] && this.mapa[31] == this.mapa[32] && this.mapa[29] != 0) return this.mapa[29];
        if (this.mapa[30] == this.mapa[31] && this.mapa[31] == this.mapa[32] && this.mapa[32] == this.mapa[33] && this.mapa[30] != 0) return this.mapa[30];
        if (this.mapa[31] == this.mapa[32] && this.mapa[32] == this.mapa[33] && this.mapa[33] == this.mapa[34] && this.mapa[31] != 0) return this.mapa[31];
        //sexta fila
        if (this.mapa[35] == this.mapa[36] && this.mapa[36] == this.mapa[37] && this.mapa[37] == this.mapa[38] && this.mapa[35] != 0) return this.mapa[35];
        if (this.mapa[36] == this.mapa[37] && this.mapa[37] == this.mapa[38] && this.mapa[38] == this.mapa[39] && this.mapa[36] != 0) return this.mapa[36];
        if (this.mapa[37] == this.mapa[38] && this.mapa[38] == this.mapa[39] && this.mapa[39] == this.mapa[40] && this.mapa[37] != 0) return this.mapa[37];
        if (this.mapa[38] == this.mapa[39] && this.mapa[39] == this.mapa[40] && this.mapa[40] == this.mapa[41] && this.mapa[38] != 0) return this.mapa[38];

        //Las líneas verticales
        // Columna uno
        if (this.mapa[0] == this.mapa[7] && this.mapa[7] == this.mapa[14] && this.mapa[14] == this.mapa[21] && this.mapa[0] != 0) return this.mapa[0];
        if (this.mapa[7] == this.mapa[14] && this.mapa[14] == this.mapa[21] && this.mapa[21] == this.mapa[28] && this.mapa[7] != 0) return this.mapa[7];
        if (this.mapa[14] == this.mapa[21] && this.mapa[21] == this.mapa[28] && this.mapa[28] == this.mapa[35] && this.mapa[14] !=0) return this.mapa[14];
        // Columna dos
        if (this.mapa[1] == this.mapa[8] && this.mapa[8] == this.mapa[15] && this.mapa[15] == this.mapa[22] && this.mapa[1] != 0) return this.mapa[1];
        if (this.mapa[8] == this.mapa[15] && this.mapa[15] == this.mapa[22] && this.mapa[22] == this.mapa[29] && this.mapa[8] != 0) return this.mapa[8];
        if (this.mapa[15] == this.mapa[22] && this.mapa[22] == this.mapa[29] && this.mapa[29] == this.mapa[36] && this.mapa[15] !=0) return this.mapa[15];
        // Columna tres
        if (this.mapa[2] == this.mapa[9] && this.mapa[9] == this.mapa[16] && this.mapa[16] == this.mapa[23] && this.mapa[2] != 0) return this.mapa[2];
        if (this.mapa[9] == this.mapa[16] && this.mapa[16] == this.mapa[23] && this.mapa[23] == this.mapa[30] && this.mapa[9] != 0) return this.mapa[9];
        if (this.mapa[16] == this.mapa[23] && this.mapa[23] == this.mapa[30] && this.mapa[30] == this.mapa[37] && this.mapa[16] !=0) return this.mapa[16];
        // Columna cuatro
        if (this.mapa[3] == this.mapa[10] && this.mapa[10] == this.mapa[17] && this.mapa[17] == this.mapa[24] && this.mapa[3] != 0) return this.mapa[3];
        if (this.mapa[10] == this.mapa[17] && this.mapa[17] == this.mapa[24] && this.mapa[24] == this.mapa[31] && this.mapa[10] != 0) return this.mapa[10];
        if (this.mapa[17] == this.mapa[24] && this.mapa[24] == this.mapa[31] && this.mapa[31] == this.mapa[38] && this.mapa[17] !=0) return this.mapa[17];
        // columna cinco
        if (this.mapa[4] == this.mapa[11] && this.mapa[11] == this.mapa[18] && this.mapa[18] == this.mapa[25] && this.mapa[4] != 0) return this.mapa[4];
        if (this.mapa[11] == this.mapa[18] && this.mapa[18] == this.mapa[25] && this.mapa[25] == this.mapa[32] && this.mapa[11] != 0) return this.mapa[11];
        if (this.mapa[18] == this.mapa[25] && this.mapa[25] == this.mapa[32] && this.mapa[32] == this.mapa[39] && this.mapa[18] !=0) return this.mapa[18];
        // Columna seis
        if (this.mapa[5] == this.mapa[12] && this.mapa[12] == this.mapa[19] && this.mapa[19] == this.mapa[26] && this.mapa[5] != 0) return this.mapa[5];
        if (this.mapa[12] == this.mapa[19] && this.mapa[19] == this.mapa[26] && this.mapa[26] == this.mapa[33] && this.mapa[12] != 0) return this.mapa[12];
        if (this.mapa[19] == this.mapa[26] && this.mapa[26] == this.mapa[33] && this.mapa[33] == this.mapa[40] && this.mapa[19] !=0) return this.mapa[19];
        // Columna siete
        if (this.mapa[6] == this.mapa[13] && this.mapa[13] == this.mapa[20] && this.mapa[20] == this.mapa[27] && this.mapa[6] != 0) return this.mapa[6];
        if (this.mapa[13] == this.mapa[20] && this.mapa[20] == this.mapa[27] && this.mapa[27] == this.mapa[34] && this.mapa[13] != 0) return this.mapa[13];
        if (this.mapa[20] == this.mapa[27] && this.mapa[27] == this.mapa[34] && this.mapa[34] == this.mapa[41] && this.mapa[20] !=0) return this.mapa[20];

        //Las diagonales
        // que locura
        // izquierda uno
        if (this.mapa[0] == this.mapa[8] && this.mapa[8] == this.mapa[16] && this.mapa[16] == this.mapa[24] && this.mapa[0] != 0) return this.mapa[0];
        if (this.mapa[7] == this.mapa[15] && this.mapa[15] == this.mapa[23] && this.mapa[23] == this.mapa[31] && this.mapa[7] != 0) return this.mapa[7];
        if (this.mapa[14] == this.mapa[22] && this.mapa[22] == this.mapa[30] && this.mapa[30] == this.mapa[38] && this.mapa[14] != 0) return this.mapa[14];
        // izquierda dos
        if (this.mapa[1] == this.mapa[9] && this.mapa[9] == this.mapa[17] && this.mapa[17] == this.mapa[25] && this.mapa[1] != 0) return this.mapa[1];
        if (this.mapa[8] == this.mapa[16] && this.mapa[16] == this.mapa[24] && this.mapa[24] == this.mapa[32] && this.mapa[8] != 0) return this.mapa[8];
        if (this.mapa[15] == this.mapa[23] && this.mapa[23] == this.mapa[31] && this.mapa[31] == this.mapa[39] && this.mapa[15] != 0) return this.mapa[15];
        // izquierda tres
        if (this.mapa[2] == this.mapa[10] && this.mapa[10] == this.mapa[18] && this.mapa[18] == this.mapa[26] && this.mapa[2] != 0) return this.mapa[2];
        if (this.mapa[9] == this.mapa[17] && this.mapa[17] == this.mapa[25] && this.mapa[25] == this.mapa[33] && this.mapa[9] != 0) return this.mapa[9];
        if (this.mapa[16] == this.mapa[24] && this.mapa[24] == this.mapa[32] && this.mapa[32] == this.mapa[40] && this.mapa[16] != 0) return this.mapa[16];
        // izquierda cuatro
        if (this.mapa[3] == this.mapa[11] && this.mapa[11] == this.mapa[19] && this.mapa[19] == this.mapa[27] && this.mapa[3] != 0) return this.mapa[3];
        if (this.mapa[10] == this.mapa[18] && this.mapa[18] == this.mapa[26] && this.mapa[26] == this.mapa[34] && this.mapa[10] != 0) return this.mapa[10];
        if (this.mapa[17] == this.mapa[25] && this.mapa[25] == this.mapa[33] && this.mapa[33] == this.mapa[41] && this.mapa[17] != 0) return this.mapa[17];
        
        // derecha uno
        if (this.mapa[6] == this.mapa[12] && this.mapa[12] == this.mapa[18] && this.mapa[18] == this.mapa[24] && this.mapa[6] != 0) return this.mapa[6];
        if (this.mapa[13] == this.mapa[19] && this.mapa[19] == this.mapa[25] && this.mapa[25] == this.mapa[31] && this.mapa[13] != 0) return this.mapa[13];
        if (this.mapa[20]== this.mapa[26] && this.mapa[26]== this.mapa[32] && this.mapa[32]== this.mapa[38] && this.mapa[20] != 0) return this.mapa[20];
        // derecha dos
        if (this.mapa[5] == this.mapa[11] && this.mapa[11] == this.mapa[17] && this.mapa[17] == this.mapa[23] && this.mapa[5] != 0) return this.mapa[5];
        if (this.mapa[12] == this.mapa[18] && this.mapa[18] == this.mapa[24] && this.mapa[24] == this.mapa[30] && this.mapa[12] != 0) return this.mapa[12];
        if (this.mapa[19] == this.mapa[25] && this.mapa[25] == this.mapa[31] && this.mapa[31] == this.mapa[37] && this.mapa[19] != 0) return this.mapa[19];
        // derecha tres
        if (this.mapa[4] == this.mapa[10] && this.mapa[10] == this.mapa[16] && this.mapa[16] == this.mapa[22] && this.mapa[4] != 0) return this.mapa[4];
        if (this.mapa[11] == this.mapa[17] && this.mapa[17] == this.mapa[23] && this.mapa[23] == this.mapa[29] && this.mapa[11] != 0) return this.mapa[11];
        if (this.mapa[18] == this.mapa[24] && this.mapa[24] == this.mapa[30] && this.mapa[30] == this.mapa[36] && this.mapa[18] != 0) return this.mapa[18];
        // derecha cuatro
        if (this.mapa[3] == this.mapa[9] && this.mapa[9] == this.mapa[15] && this.mapa[15] == this.mapa[21] && this.mapa[3] != 0) return this.mapa[3];
        if (this.mapa[10] == this.mapa[16] && this.mapa[16] == this.mapa[22] && this.mapa[22] == this.mapa[28] && this.mapa[10] != 0) return this.mapa[10];
        if (this.mapa[17] == this.mapa[23] && this.mapa[23] == this.mapa[29] && this.mapa[29] == this.mapa[35] && this.mapa[17] != 0) return this.mapa[17];
        
        if (numEspacios > 0) {
          return 0;
        } else {
          return 3;
        }
      }
    }
  }

</script>

<style>
 #app {

    font-family: 'Griffy', cursive;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 30px;
  }

  h1,
  h2 {
    font-weight: normal;
  }

  .red {
    background-color: palevioletred;
    border-radius: 8px;
  }

  .casilla {
    width: 70px;
    height: 70px;
    font-size: 35px;
  }

  .espace {
    padding-top: 15px;
  }

  .headerGrid {
    display: grid;
    grid-gap: 15px;
    grid-template-columns: 2fr 5fr 2fr;
    text-align: center;
  }

  .logo {
    height: 80px;
    width: 80px;
  }

  table {
    background-color: palegreen;
    border-style: 2px double black;
  }


</style>
