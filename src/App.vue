<template>
  <div id="app">
    <div class="titulostyle">
      <h1>{{ mensaje }} </h1>
      Titulo:<input v-model="titulo"> <br/><br/>
    </div>

    <div class="cuerpostyle">
      <label for="filtro">Filtro:</label>
      <select name="filtro" id="filtro" v-model="filtroseleccionado">
        <option v-for="(tipo,index) in filtro" v-bind:key="index" v-bind:value="tipo.valor">{{ tipo.texto }}</option>
        </select><br/><br/>
        <label for="colortexto">Color:</label>
      <select class="inlinee" name="colortexto" id="colortexto" v-model="colorseleccionado">
        <option v-for="(elcolor,index) in colortexto" v-bind:key="index" v-bind:value="elcolor.valor">{{ elcolor.texto }}</option>
        </select><div class="circulo" v-bind:style="{'background-color':colorseleccionado}"></div><br/><br/>
        Tamaño:<input v-model="tamano">  <br/><br/>
    </div>

    <div class="btnstyle">
          <button v-on:click="enviaralhijo">Obtener mi gatito</button><br/>
        <Randomcat v-bind:eltitulo="tituloaenviar" v-bind:elfiltro="filtroaenviar" v-bind:elcolor="coloraenviar" v-bind:eltamano="tamanoaenviar"/>
    </div>
  </div>
</template>

<script>
import Randomcat from './components/Randomcat.vue'

export default {
  name: 'App',
  components: {
    Randomcat
  },
  data(){
    return{
      mensaje: 'Random Gif Cat',
      titulo:'',
      tituloaenviar:'',
      filtro:[
      {texto:'Blur', valor:'blur',},
      {texto:'Mono', valor:'mono',},
      {texto:'Sepia', valor:'sepia',},
      {texto:'Negative', valor:'negative',},
      {texto:'Paint', valor:'paint',},
      {texto:'Pixel', valor:'pixel',},
      ],
      filtroseleccionado: '',
      filtroaenviar: '',
      colortexto:[
      {texto:'Rojo', valor:'red',},
      {texto:'Verde', valor:'green',},
      {texto:'Blue', valor:'blue',},
      {texto:'Amarillo', valor:'yellow',},
      {texto:'Purpura', valor:'purple',},
      {texto:'Rosado', valor:'pink',},
      ],
      colorseleccionado: '',
      coloraenviar: '',
      tamano:'',
      tamanoaenviar: '',
    }
  },
  methods:{
    enviaralhijo: function(){
      this.tituloaenviar = this.titulo;
      this.filtroaenviar = this.filtroseleccionado;
      this.coloraenviar = this.colorseleccionado;
      this.tamanoaenviar = this.tamano;

      setTimeout(()=>{
        this.tituloaenviar = '';
        this.titulo = '';
        this.filtroaenviar = '';
        this.filtroseleccionado = '';

      }, 1000);


    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px;

}
.titulostyle, .btnstyle {
background-color: salmon;
padding: 20px;
}
.cuerpostyle {
background-color: #1FD8DF;
padding: 20px;
}
.circulo {
    width: 20px;
    height: 20px;
    -moz-border-radius: 50%;
    -webkit-border-radius: 50%;
    border-radius: 50%;
    background: white;
    position: absolute;
    display: inline;
    margin-left: 5px;
}
.inlinee {
position: relative;

}
</style>
