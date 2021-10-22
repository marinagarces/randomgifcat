<template>
  <div class="Randomcat">
  <p>{{ escucharprops }}</p>
  <p>{{ elfiltro }}</p>
  <p>{{ elcolor }}</p>
  <p>{{ eltamano }}</p>
  <div>
    <img v-bind:src="respuestaapi" >
  </div>
  </div>
</template>

<script>
export default {
  name: 'Randomcat',
  props: {
    eltitulo: String,
    elfiltro: String,
    elcolor: String,
    eltamano: String,
  },
  data(){
    return{
      respuestaapi:'',
    }
  },
  computed: {
    escucharprops:function(){
      if(!this.eltitulo==''){
        this.consumirapigatos();
      }
      return this.eltitulo;
    }
  },
  methods:{
    consumirapigatos(){
      this.respuestaapi = 'Cargando...';
      fetch('https://cataas.com/cat/gif')
        .then(response=> {console.log(response)
          this.respuestaapi = response.url});

    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.Randomcat{

}

</style>
