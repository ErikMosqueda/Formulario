<script>
  import axios from 'axios'
  import insertarObjetivos from '../components/agregarObjetivos.vue'
  import InputText from '../components/InputText.vue'
  
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
        Personalidad1: "50",
        Personalidad2: "50",
        Personalidad3: "50",
        Personalidad4: "50",
        Objetivos: [],
        Frustraciones: [],
        Motivaciones: [],
        Marcas: " "
  
      }
    },
  
    mounted() {
    },
    components: {
      insertarObjetivos,
      InputText
    },
    emits: ['informacion'],

  
    methods: {
      
      AsignacionNombre(s){
        this.Nombre = s
        console.log(this.Nombre)
      },
      AsignacionEdad(s){
        this.Edad = s
        console.log(this.Edad)
      },
      AsignacionTrabajo(s){
        this.Trabajo = s
        console.log(this.Trabajo)
      },
      AsignacionCita(s){
        this.Cita = s
        console.log(this.Cita)
      },
      AsignacionResidencia(s){
        this.Residencia = s
        console.log(this.Residencia)
      },
      AsignacionCitaAutor(s){
        this.CitaAutor = s
        console.log(this.CitaAutor)
      },
      
      
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
            <!-- <input type="text" name="nombre" id="nombre" v-model="Nombre" class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2"> -->
            <InputText @informacion="AsignacionNombre"></InputText>
            <label for="edad"> Edad: </label>
            <!-- <input type="text" name="edad" id="edad" v-model="Edad" class="px-2 py-1 rounded-lg mb-3 ml-2"> -->
            <InputText @informacion="AsignacionEdad"></InputText>
            <div>
                <label for="trabajo"> Trabajo: </label>
                <InputText @informacion="AsignacionTrabajo"></InputText>

                <label for="residencia"> Residencia: </label>
                <InputText @informacion="AsignacionResidencia"></InputText>
          
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
          <label class="font-bold text-2xl mb-3">Sentimientos y emociones</label>
          <div class="flex mt-2">

              <!-- PERSONALIDADES -->
            <div class="flex grid-cols-2">
              <div></div>

              <div class="ml-5 ">
                <p class="font-bold">Personalidades</p>
                <div>
                  <label for="personalidad01"> Personalidad 1: </label>
                  <input type="range" name="Personalidad1" id="Personalidad1" v-model="Personalidad1" class="">
                  {{Personalidad1 }}%
                </div>

                <div>
                  <label for="personalidad02"> Personalidad 2: </label>
                  <input type="range" name="Personalidad2" id="Personalidad2" v-model="Personalidad2" class="">
                  {{Personalidad2 }}%
                </div>

                  
                <div>
                  <label for="personalidad03"> Personalidad 3: </label>
                  <input type="range" name="Personalidad3" id="Personalidad3" v-model="Personalidad3" class="">
                  {{Personalidad3 }}%
                </div>
                  
                <div>
                  <label for="personalidad04"> Personalidad 4: </label>
                  <input type="range" name="Personalidad4" id="Personalidad4" v-model="Personalidad4" class="">
                  {{Personalidad4 }}%
                </div>
                  
              </div>

            </div>

              <!-- CITA AUTOR CONTENIDO -->
            <div class=" ml-6 mr-2">
              <div>
                <label for="cita"> Cita: </label>
                <InputText @informacion="AsignacionCita"></InputText>
              </div>
              
              <div>
                <label for="citaAutor"> Autor: </label>
                <InputText @informacion="AsignacionCitaAutor"></InputText>
              </div>

            </div>       
            

          </div>

          
          <div>
            <label for="objetivos"> Objetivos: </label>
            <input type="text" name="Objetivos" id="Objetivos" v-model="Objetivos" class="px-2 py-1 rounded-lg mb-3 ml-2">
            //<insertarObjetivos>Insertar</insertarObjetivos>
            
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


