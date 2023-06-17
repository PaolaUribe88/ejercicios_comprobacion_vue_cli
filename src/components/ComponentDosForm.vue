<template>
    <div id="ComponenteFormulario">
        <h1>Formulario </h1>
        <div id="FormPadre">
            <div id="IzqForm">
                <form>
                    <label for="txtNombre">Nombre:</label>
                    <input type="text" id="txtNombre" v-model="nombre"> <br>
                    <label for="txtApellido">Apellido:</label>
                    <input type="text" id="txtApellido" v-model="apellido"><br>
                    <label for="txtEdad">Edad:</label>
                    <input type="text" id="txtEdad" v-model="edad"><br>
                    <label for="txtCorreo">Correo:</label>
                    <input type="text" id="txtCorreo" v-model="correo"><br>
                    <input type="submit" id="btnEnviar" value="Enviar" v-on:click.prevent="procesarDatos">
                </form>
                
            </div>
            <div id="DerechaForm">
                <form>
                    <p id="parrafoSaludo">Información: {{ mensajeSalida }}</p>
                    <p id="parrafoEdad">Edad: {{  mensajeEdad }}</p> 
                </form>
                
            </div>

      </div>
    
           

    </div>
</template>
<script>
    export default{
    name:'SesionDosComponent',
    data:function(){
        return{
            nombre:'',
            apellido:'',
            edad:'',
            correo:'',
            mensajeSalida:'',
            mensajeEdad:'',
        }
    },
    methods:{
        procesarDatos: function(){
            this.mensajeSalida = `Hola ${this.nombre} ${this.apellido}, el correo registrado es ${this.correo}`;
            let edadNumero = Number(this.edad);
            let catalogado='';
            if(edadNumero>=0 && edadNumero<=13){
                catalogado= 'Niñez';
            }else if(edadNumero>=14 && edadNumero<=17){
                catalogado= 'Adolescente'; 
            }else if(edadNumero>=18 && edadNumero<=35){
                catalogado= 'Adulto Jóven';
            }else if(edadNumero>=36 && edadNumero<=64){
                catalogado= 'Adulto';
            }else{
                catalogado= 'Adulto Mayor';
            }

            this.mensajeEdad = `La catalogación de su edad ${this.edad} es ${catalogado}`;
        },
    },
}
</script>
<style scoped>
#ComponenteFormulario{
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
#button{
        background-color: aquamarine;
        border-radius: 10px;
    }
#parrafoSaludo{
    font-size: 30px;
}
#parrafoEdad{
    font-size: 25px;
}

</style>