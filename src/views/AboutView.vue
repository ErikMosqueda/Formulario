<script>
  import axios from 'axios'
  import InputText from '../components/InputText.vue'
  import InputTextArea from '../components/InputTextArea.vue'
  import InputObjetivo from '../components/inputObjetivos.vue'
  import InputFrustracion from '../components/inputFrustraciones.vue'
  import InputMotivaciones from '../components/inputMotivaciones.vue'
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
        newObjetivo:'',
        newFrustracion:'',
        newMotivacion:'',
        Objetivos: [{value:''}],
        Frustraciones: [{value:''}],
        Motivaciones: [{value: '','porcentaje':''}],
        Marcas: " ",
        contadorObjetivos: 1,
        contadorFrustaciones: 1,
        contadorMotivaciones: 1,
  
      }
    },
  
    mounted() {
    },
    components: {
      InputText,
      InputTextArea,
      InputObjetivo,
      InputFrustracion,
      InputMotivaciones
   
    },
    emits: ['informacion','informacionTextArea','informacionSelect'],

  
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
      AsignacionMarcas(s){
        this.Marcas = s
        console.log(this.Marcas)
      },
      AsignacionBio(s){
        this.Bio = s
        console.log(this.Bio)
      },
      AsignacionObjetivos(s, index){
      this.Objetivos[index] = {value: s}
      console.log(this.Objetivos)
    },
      AsignacionFrustraciones(s, index){
      this.Frustraciones[index] = {value: s}
      console.log(this.Frustraciones)
    },
    AsignacionMotivaciones(s,m, index){
      this.Motivaciones[index] = {value: s,porcentaje: m}
      console.log(this.Motivaciones)
    },
    
      
      soloLetras(e){
        console.log(e)

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
        
      },
       
    },
  }
  
  </script>
  
  <template >
    <div class="center  justify-center flex text-center">
      <div class=" md:w-1-1 w-4/4 lg:w-3/4 px-4 py-4 justify-center card-flex text-center items-center shadow-sm bg-gray-300 rounded-lg ">
        <form >
          <label class="font-bold text-2xl">Informacion personal</label>
          <div class=" mt-3 mb-3  justify-center text-center">
            <div class="flex justify-center">
              <div>
                <label for="nombre"> Nombre: </label>
                <InputText @informacion="AsignacionNombre"></InputText>
                <p v-if="Nombre == '' " class="text-red-500"> Ingresa este campo</p>
              </div>

              <div>
                  <label for="edad"> Edad: </label>
                  <InputText @informacion="AsignacionEdad" ></InputText>
                  <p v-if="Edad >=100" class="text-red-500"> Edad inválida</p>
                  <p v-if="Edad == 0" class="text-red-500"> Edad inválida</p>
                  <p v-if="Edad == '' " class="text-red-500"> Ingresa este campo</p>
              </div>
            </div>
            
            <div class="flex justify-center">
                <div class="">
                  <label for="trabajo"> Trabajo: </label>
                  <InputText @informacion="AsignacionTrabajo"></InputText>
                  <p v-if="Trabajo == '' " class="text-red-500"> Ingresa este campo</p>
                </div>

                <div>
                  
                  <label for="residencia"> Residencia: </label>
                  <InputText @informacion="AsignacionResidencia"></InputText>
                  <p v-if="Residencia == '' " class="text-red-500"> Ingresa este campo</p>
                </div>

                
            </div>
          
            
            
            <div class="mr-5 justify-center flex">
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

            <div class="mt-3 justify-center">
              <div>
                <label for="bio"> Biografía: </label>
              </div>
              <div>
                <InputTextArea @informacionTextArea="AsignacionBio"></InputTextArea>
                <p v-if="Bio == '' " class="text-red-500"> Ingresa este campo</p>
              </div>
              
                
            </div>


          </div>
          
          <label class="font-bold text-2xl mb-3">Sentimientos y emociones</label>
          
          
          <div class="flex justify-center mt-2">

            <div>
              <div>
                <label for="cita"> Cita: </label>
                <InputText @informacion="AsignacionCita"></InputText>
                <p v-if="Cita == '' " class="text-red-500"> Ingresa este campo</p>
              </div>
            </div>

            <div>

              <div>
                <label for="citaAutor"> Autor: </label>
                <InputText @informacion="AsignacionCitaAutor"></InputText>
                <p v-if="CitaAutor == '' " class="text-red-500"> Ingresa este campo</p>
              </div>
            </div>
          
            <div>
              <div>
                <label for="marcas"> Marcas: </label>
                <InputText @informacion="AsignacionMarcas"></InputText>
                <p v-if="Marcas == '' " class="text-red-500"> Ingresa este campo</p>
              </div>
            </div>

              <!-- CITA AUTOR CONTENIDO -->
                  
            

          </div>
            <!-- APARTADO DE MOTIVACIONES Y OBEJTIVOS -->
          <div class=" flex justify-center">
            <div>
                <label for="motivaciones" class="text-xl"> Objetivos: </label> 
                <div v-for="(obj, index) in Objetivos">
                  <InputObjetivo @informacion="AsignacionObjetivos" :index="index"> </inputObjetivo>
                  <p v-if="Objetivos == '' " class="text-red-500"> Ingresa este campo</p>
       
                </div>
                <button v-on:click.prevent="this.Objetivos.push(newObjetivo)" class="px-4 py-2 mb-2 bg-gray-600 text-white rounded"> Agregar</button>
            </div>

            <div>
               <label for="frustraciones" class="text-xl"> Frustraciones: </label> 
                <div v-for="(obj, index) in Frustraciones">
                  <InputFrustracion @informacion="AsignacionFrustraciones" :index="index"> </InputFrustracion>
                  
       
                </div>
                <button v-on:click.prevent="this.Frustraciones.push(newFrustracion)" class="px-4 py-2 mb-2 bg-gray-600 text-white rounded"> Agregar</button> 
            </div>


          </div>
          
          <div>
            <div class=" justify-center flex mt-5">
              <div></div>

              <div class="ml-5">
                <p class="font-bold">Personalidades</p>
                <div>
                  <label for="personalidad01" class="text-2xl"> Mente: </label>
                  <input type="range" name="Personalidad1" id="Personalidad1" v-model="Personalidad1" class="">
                  {{Personalidad1 }}%
                </div>

                <div>
                  <label for="personalidad02" class="text-2xl"> Energía: </label>
                  <input type="range" name="Personalidad2" id="Personalidad2" v-model="Personalidad2" class="">
                  {{Personalidad2 }}%
                </div>

                  
                <div>
                  <label for="personalidad03" class="text-2xl"> Naturaleza: </label>
                  <input type="range" name="Personalidad3" id="Personalidad3" v-model="Personalidad3" class="">
                  {{Personalidad3 }}%
                </div>
                  
                <div>
                  <label for="personalidad04" class="text-2xl"> Tácticas: </label>
                  <input type="range" name="Personalidad4" id="Personalidad4" v-model="Personalidad4" class="">
                  {{Personalidad4 }}%
                </div>
                  
              </div>

              <div>
                <label for="motivaciones" class="text-xl"> Motivaciones: </label> 
                <div v-for="(obj, index) in Motivaciones">
                  <InputMotivaciones @informacion="AsignacionMotivaciones" :index="index"> </InputMotivaciones>
                
                </div>
                <button v-on:click.prevent="this.Motivaciones.push(newMotivacion)" class="px-4 py-2 mb-2 bg-gray-600 text-white rounded"> Agregar</button>
                  <!-- AGREGA EL BOTON -->
              </div>

            </div>
          </div>
         
 
                   
          <div class="flex justify-center mt-6">
            <button @click="Registro" class="px-4 py-2 bg-green-400 text-white rounded hover:bg-green-600"
            v-if=" Edad <100 && Edad != '' && Marcas != '' ">
            Enviar
          </button>
          </div>
          
        </form>
        <div class="bg-green-300">
        </div>
      </div>
    </div>
  </template>


