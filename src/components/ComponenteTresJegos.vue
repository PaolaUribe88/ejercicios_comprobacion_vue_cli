<template>
    <div id="ComponenteJuegos">
        <h1>Juegos </h1>
        <div id="FormPadre">
            <div id="IzqForm">
                <table border="1">
                    <tr>
                        <th>#</th><th>Juego</th><th >Eliminar Juego</th>
                        
                    </tr>
                    <tr v-for="(juegos, index) in juegos" :key="index">
                        <td>{{ index }}</td> <td>{{ juegos }}</td><td><button v-on:click="eliminarJuego" >Eliminar</button ></td>
                    </tr>

                </table><br>
                <form>
                    <label for="txtNombreJuego">Nombre Juego:</label>
                    <input type="text" id="txtNombreJuego" v-model="nombreJuegoAInsertar"><br>
                    <button v-on:click.prevent="insertarJuego">Insertar el Juego</button>
                    
                </form>
            </div>
          
        </div>
    </div>
</template>
<script>
export default{
    name:'ComponenteTresJegos',
    props:{
        juegos:{
            type: Array,
            required: true,
        }
    },
    data: function(){
        return{
            nombreJuegoAInsertar:'',
        }
    },
    methods:{
        eliminarJuego: function(indice){
            this.$emit('juegoAEliminar', indice);
        },
        insertarJuego: function(){
            this.$emit('juegoAInsertar', this.nombreJuegoAInsertar);
            this.nombreJuegoAInsertar = '';
        },
    },

}


</script>

<style scoped>
#ComponenteJuegos{
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px; 
    width: 80%; 
    margin:0 auto; 
    background-color:rgb(174, 201, 232); 
    color:rgb(7, 7, 7);
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
    width: 96%;
    background-color: rgb(255, 0, 183);
    border: 3px solid rgb(37,86,150); 
    border-radius:10px; 
    padding:10px;  
    margin:0 auto; 
    color:white;
}
#button{
        background-color: aquamarine;
        border-radius: 10px;
    }
    input{
        background-color: aquamarine;
        border-radius: 10px;
    }


</style>