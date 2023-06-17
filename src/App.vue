<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ComponentDosForm>
    </ComponentDosForm>
    <hr>
    <ComponenteTresJegos
    v-bind:juegos="arregloJuegos"
      v-on:juegoAEliminar = "eliminarDelArregloJuegos"
      v-on:juegoAInsertar = "insertarJuegoEnElArreglo">

    </ComponenteTresJegos>
    <hr>
    <ComponenteCuatroGaleria
      v-bind:imagenes="arregloImagenes"
      v-bind:descripciones="arregloDescripciones"
      v-bind:autores="arregloAutores"
      v-bind:images_src = "arregloImagenes"
      v-on:add ="agregarImagen"
      v-on:delete="eliminarImagen">
      <p>Esto es parte del Componente Padre</p>>

    </ComponenteCuatroGaleria>
 
  </div>

</template>

<script>

import ComponentDosForm from './components/ComponentDosForm.vue';
import ComponenteCuatroGaleria from './components/ComponenteCuatroGaleria.vue';
import ComponenteTresJegos from './components/ComponenteTresJegos.vue'
export default {
  name: 'App',
  components: {
    ComponentDosForm,
    ComponenteCuatroGaleria,
    ComponenteTresJegos,

 
  },
  data: function(){
    return{
      arregloJuegos:['Arena of Valor', 'Pokemon Unite', 'Donkey Kong', 'Heroes of the Storm', 'Valorant'],
      arregloImagenes: [ 
        "https://fotos.perfil.com/2021/10/21/trim/1280/720/volver-al-futuro-1252579.jpg", 
        "https://www.clarin.com/img/2019/11/27/qt2yQrHl_720x0__1.jpg",
        
      ],
      arregloDescripciones:[
        'Marty Mcfly',
        'Portada',
        'Automovil'
      ],
      arregloAutores:[
        'Google',
        'Google',
        'Wikipedia',
      ],
    }
  },
 
  methods:{ 
    eliminarDelArregloJuegos:function(indiceJuego){
      this.arregloJuegos.splice(indiceJuego,1);
    },
    insertarJuegoEnElArreglo: function(nombreJuego){
      this.arregloJuegos.push(nombreJuego);
    },
    agregarImagen(src){ 
      this.arregloImagenes.push(src); 
    },
      eliminarImagen(index){ 
      this.arregloImagenes.splice(index,1); 
    },
}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
