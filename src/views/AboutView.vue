<script>
  import axios from 'axios'
  
  export default {
  
    data() {
      return {
        
        Nombre: '',
        Edad:  '',
        EstadoCivil: " ",
        Trabajo:" ",
        Residencia: " ",
        Cita: " ",
        CitaAutor: " ",
        Bio: " ",
        Personalidad1: " ",
        Personalidad2: " ",
        Personalidad3: " ",
        Personalidad4: " ",
        Objetivos: [],
        Frustraciones: [],
        Motivaciones: [],
        Marcas: " "
  
      }
    },
  
    mounted() {
    },
  
    methods: {
      
      Registro() {  
        axios
        .post("/api/guardarPersonasUxd.php", {
  
            nombre: this.Nombre,
            edad: this.Edad,
            estadoCivil: this.EstadoCivil,
            trabajo: this.Trabajo,
            residencia: this.Residencia,
            cita: this.Cita,
            citaAutor: this.CitaAutor,
            bio: this.Bio,
            personalidad01: this.Personalidad1,
            personalidad02: this.Personalidad2,
            personalidad03: this.Personalidad3,
            personalidad04: this.Personalidad4,
            objetivos: this.Objetivos,
            frustraciones: this.Frustraciones,
            motivaciones: this.Motivaciones,
            marcas: this.Marcas
          
          })
          .then((response) => {
          console.log(response.status)
          });
        
      }
    },
  }
  
  </script>
  
  <template>
    <div class="center  justify-center flex">
      <div class=" px-4 py-4 justify-center card-flex shadow-sm bg-gray-300 rounded-lg ">
        <form >
          <label class="font-bold text-2xl">Informacion personal</label>
          <div class=" mt-3 mb-3">
            <label for="nombre"> Nombre: </label>
            <input type="text" name="nombre" id="nombre" v-model="Nombre" class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2">
          
            <label for="edad"> Edad: </label>
            <input type="text" name="edad" id="edad" v-model="Edad" class="px-2 py-1 rounded-lg mb-3 ml-2">

            <div>
                <label for="trabajo"> Trabajo: </label>
                <input type="text" name="Trabajo" id="Trabajo" v-model="Trabajo" class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2">

                <label for="residencia"> Residencia: </label>
                <input type="text" name="Residencia" id="Residencia" v-model="Residencia" class="px-2 py-1 rounded-lg mb-3 ml-2">
          
            </div>
            
            <div class="mr-5 text-center flex">
              <div>
                <div>
                  <label for="estadoCivil"> Estado civil: </label>
                </div>
                <div>
                  <select name="EstadoCivil" id="EstadoCivil" v-model="EstadoCivil">
                <option value="1">Soltero</option>
                <option value="2">Casado</option>
                <option value="3">Divorciado</option>
                <option value="4">Separado</option>
                <option value="5">Union libre</option>
                <option value="6">Viudo</option>
                </select>
                </div>
              </div>
        
            </div>

            <div class="mt-3">
              <div>
                <label for="bio"> Biografía: </label>
              </div>
              <div>
                <textarea type="text" name="Bio" id="Bio" v-model="Bio" class="px-2 py-1 rounded-lg mb-3 ml-2 mt-2"
                rows="5" cols="50">
                </textarea>
              </div>
              
                
            </div>


          </div>
          <label class="font-bold text-2xl">Sentimientos y emociones</label>
          <div class="">
            <div class="flex bg-green-600 grid-cols-2">
              <div></div>

              <div class="ml-5 ">
                <p class="font-bold">Personalidades</p>
                <div>
                  <label for="personalidad01"> Personalidad 1: </label>
                  <input type="text" name="Personalidad1" id="Personalidad1" v-model="Personalidad1" class="px-2 py-1 rounded-lg mb-3 ml-2">
                </div>

                <div>
                  <label for="personalidad02"> Personalidad 2: </label>
                  <input type="text" name="Personalidad2" id="Personalidad2" v-model="Personalidad2" class="px-2 py-1 rounded-lg mb-3 ml-2">
                </div>
                  
                <div>
                  <label for="personalidad03"> Personalidad 3: </label>
                  <input type="text" name="Personalidad3" id="Personalidad3" v-model="Personalidad3" class="px-2 py-1 rounded-lg mb-3 ml-2">
                </div>
                  
                <div>
                  <label for="personalidad04"> Personalidad 4: </label>
                  <input type="text" name="Personalidad4" id="Personalidad4" v-model="Personalidad4" class="px-2 py-1 rounded-lg mb-3 ml-2">
                </div>
                  
              </div>

            </div>
          </div>

          <div>
            <label for="cita"> Cita: </label>
            <input type="text" name="Cita" id="Cita" v-model="Cita" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>

          <div>
            <label for="citaAutor"> Autor de la cita: </label>
            <input type="text" name="CitaAutor" id="CitaAutor" v-model="CitaAutor" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>


          <div>
            <label for="objetivos"> Objetivos: </label>
            <input type="text" name="Objetivos" id="Objetivos" v-model="Objetivos" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>

          <div>
            <label for="frustraciones"> Frustaciones: </label>
            <input type="text" name="Frustaciones" id="Frutaciones" v-model="Frustraciones" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>

          <div>
            <label for="motivaciones"> Motivaciones: </label>
            <input type="text" name="Motivaciones" id="Motivaciones" v-model="Motivaciones" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>

          <div>
            <label for="marcas"> Marcas: </label>
            <input type="text" name="Marcas" id=" Marcas" v-model="Marcas" class="px-2 py-1 rounded-lg mb-3 ml-2">
          </div>
 
                    
          <div class="flex justify-center">
            <button @click="Registro" class="px-4 py-2 bg-green-200 text-white rounded hover:bg-green-600">
            Enviar
          </button>
          </div>
          
        </form>
      </div>
      
    </div>
    
  </template>


