<script>
    import axios from 'axios'
    let API_URL = `api/getPersonasUxd.php`
    export default {
      data() {
        return {
          info: [],
          personajes: [],
          personajesEncontrados: "",
          buscar: '',
          siguiente:null,
          anterior:null,
          pagina:1,
          cont:2,
          contador:2,
        }
      },
      props:{},
      computed: {
 
      },
      mounted() {
        axios.get(API_URL)
          .then((response) => {
            this.info = response.data.personas;
            console.log(response.data.personas)
            
            
          })
          
      },
      methods: {
        asignacionNombres(){
          this.personajesEncontrados+="23"          
          console.log(personajesEncontrados)
        }


      },
    }
    </script>
<template>
   
    <div class=" sm:grid-cols-1 lg:flex xl:flex justify-center">
        <div class="bg-gray-300 justify-center text-center mr-6" ><!-- ESPACIO IZQUIERDO  -->
            <div class="bg-red-200 px-2 py-2">
                ESTE ESPACIO ES PARA LA FOTO
            </div>
            <div>
                <h1>NOMBRE</h1>
            </div>
            <div class="bg-green-300">
                <h1>Informacion personal</h1>
                Nombre<br>
                edad<br>
                Trabajo<br>
                RESIDENCIA<br>
                Biografia<br>


            </div>
        </div>
        <div class="col-span-2 bg-gray-200"><!-- ESPACIO DERECHO -->
            <div class="bg-green-300 text-center">
                <div class="px-2 py-2"><h1>CITA</h1></div>
            </div>

            <div>
                <h1>Objetivos</h1>
            </div>

            <div>
                Frustaciones
            </div>

            <div>
                FMotivaciones
            </div>

            <div>
                Personalidades
            </div>
        </div> 
        
      </div>
</template>