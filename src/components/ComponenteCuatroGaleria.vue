<template>
    <div id="galleryApp">
        <h1>Galeria de Imagenes</h1>
        <div id="FormPadre">
            <div id="IzqForm">
                <div class="divImagenes" v-for="(imagen,index) in imagenes">
                    <img class="contenedorImagenes"  v-bind:src="imagen" v-bind:alt="index" v-on:click="describirImagen">
                </div>
            </div>
            <div id="DerechaForm">
                <div id="contenedorPadreDescripcion">
                    <div id="descripcionIzquierda">
                                    <!--
                                    <p>{{  imagenSeleccionada }}</p>
                                    -->
                            <img class="contenedorImagenSeleccionada" v-bind:src="imagenSeleccionada" v-bind:alt="descripcionSeleccionada"><br>
                            <button v-on:click="cerrarDescripcion">Cerrar</button>
                    </div>
                        <form>
                            <h1>Agrega tus Imagenes</h1>
                            <label for="nuevaImagen">Ingrese una imagen de internet:</label>
                            <input type="text" id="nuevaImagen" v-model="newImage">
                            <button v-on:click.prevent="agregar">Agregar</button>
                            <!-- <button v-on:click.prevent="describirImagen">describir</button> -->
                            <button v-on:click.prevent="eliminar">Eliminar</button>
                        </form>
                    <div id="descripcionDerecha">
                        <p>{{ descripcionSeleccionada}}</p>
                        <p>{{ autorSeleccionado }}</p>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>
<script>
   export default{
    name:'SesionCuatroComponent',
    props:{
        imagenes:{
            type:Array,
            required: true,
        },
        descripciones:{
            type: Array,
        },
        autores:{
            type:Array,
        }
    },
    data:function(){
        return{
            hayClick:false,
            imagenSeleccionada:'',
            descripcionSeleccionada:'',
            autorSeleccionado:'',
            newImage:'',
        }
    },
    methods:{
        describirImagen: function(event){
            this.hayClick = true;
            // console.log(event);
            let indiceDeLaImagen= Number(event.target.alt);
            this.imagenSeleccionada = this.imagenes[indiceDeLaImagen];
            this.descripcionSeleccionada = this.descripciones[indiceDeLaImagen];
            this.autorSeleccionado = this.autores[indiceDeLaImagen];
        },
        cerrarDescripcion: function(){
            this.imagenSeleccionada = '';
            this.descripcionSeleccionada='',
            this.autorSeleccionado='',
            this.hayClick = false;
        },
        agregar: function(){
            this.$emit('add', this.newImage);
            },
            eliminar: function(){
                this.$emit('delete', this.index );
            }

    }
}
       
</script>

<style scoped>
#galleryApp{
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px; 
    width: 80%; 
    margin:0 auto; 
    background-color:rgb(174, 201, 232); 
    color:rgb(7, 7, 7);
    display: inline-block;
}
#FormPadre{
    text-align: left;
    display: inline-block;
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px; 
    width: 90%; 
    margin:0 auto; 
    background-color:rgb(58,136,226); 
    color:white;

}
#IzqForm{
    display: inherit;
    width: 48%;
    background-color: rgb(255, 0, 183);
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px;  
    margin:0 auto; 
    color:white;
}
#DerechaForm{
    display: inherit;
    width: 45%;
    background-color: rgb(255, 0, 183);
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px;  
    margin:0 auto; 
    color:white;
}
form{
    margin: 20px;
} 
    img{ 
        display:inline-block; 
        width: 40%;
        border-radius:10%; 
        margin-right: 10px;
        border: 3px solid rgb(194, 209, 236);
    }
    button{
        background-color: aquamarine;
        border-radius: 10px;
    }
    input{
        background-color: aquamarine;
        border-radius: 10px;
    }
</style>