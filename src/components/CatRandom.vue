<template>
  <div>
    <h1 class="titulo-gatos">Random Gif Cat</h1>
    <form @submit.prevent="infoformulario">
      <div class="inputs-formulario">
        <div class="titulo-img">
          <label>Título: </label>
          <input type="text" v-model="titulo" />
        </div>
        <div class="filtro-img">
          <label>Filtro: </label>
          <select v-model="filtro">
            <option value="blur">Blur</option>
            <option value="mono">Mono</option>
            <option value="sepia">Sepia</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
          </select>
        </div>
        <div class="color-img">
          <label>Color: </label>
          <select v-model="color">
            <option value="red">Rojo</option>
            <option value="blue">Azul</option>
            <option value="green">Verde</option>
            <option value="white">Blanco</option>
            <option value="yellow">Amarillo</option>
          </select>
          <span class="circulo" :class="{redC: color == 'red', blueC: color == 'blue', greenC: color == 'green', whiteC: color == 'white', yellowC: color == 'yellow'}"></span>
        </div>
        <div class="tamaño-img">
          <label>Tamaño: </label>
          <input v-model="tamaño" type="text" />
        </div>
      </div>
      <div class="div-boton">
        <button type="submit" class="boton-gatitos">Obtener mi gatito</button>
        <div class="agregando-img__gatito" v-if="(this.imagen)">
          <img :src="`${this.imagen}`" class="imagen-url">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "CatRandom",
  data() {
    return {
      titulo: "",
      filtro: "sepia",
      color: "red",
      tamaño: "",
      imagen: "",
    }
  },
  methods: {
    infoformulario() {
      fetch(`https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamaño}`)
      .then(result => {
        this.imagen = result.url;
      })
      .catch(error => console.error(error));
     this.titulo = "";
     this.tamaño = "";
    },
  },
};
</script>

<style scoped>
.titulo-gatos {
  background-color: rgb(175, 237, 241);
  padding: 10px;
  text-align: center;
  font-size: 80px;
}
.inputs-formulario {
  text-align: center;
  background-color: rgb(252, 155, 155);
}
.titulo-img{
  padding: 5px;
  padding-top: 10px;
}
.filtro-img{
  padding: 5px;
  padding-right: 85px;
}.color-img{
  padding: 5px;
  padding-right: 60px;
}
.tamaño-img{
  padding: 5px;
  padding-bottom: 10px;
}
.boton-gatitos{
  margin-top: 10px;
  margin-bottom: 10px;
  padding: 5px;
}
.div-boton{
  text-align: center;
  background-color: rgb(175, 237, 241);
  padding-bottom: 10px;
}
.imagen-url{
  margin-top: 10px;
  margin-bottom: 40px;
}
.circulo {
  width: 12px;
  height: 12px;
  display: inline-block;
  margin-left: 15px;
  border-radius: 50%;
}
.redC {
  background-color: red;
}
.blueC {
  background-color: blue;
}
.greenC {
  background-color: green;
}
.whiteC {
  background-color: white;
}
.yellowC {
  background-color: yellow;
}
</style>
