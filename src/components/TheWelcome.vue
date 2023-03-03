<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>

<template>
  <div class="flex">
    <div class="w-2/5 ">
      <h2 class="text-center text-3xl font-italic font-bold"> Registro de personalidad</h2>
      <img class="rounded-lg mb-3 mt-6 mb-4" src='../assets/portada.png' alt="">
      
    </div>
    
    <div class="about ml-5  w-3/5">
      <h1 class=" text-black text-3xl font-bold">¿Por qué?</h1><br>
        <p class="font-serif ml-5 mr-6 mb-5 text-3xl">Conocer nuestra personalidad, es tener conciencia 
          de nuestro modo habitual de funcionar e interaccionar con las personas y situaciones que nos 
          rodean, es reconocer nuestras tendencias, para así, poder trabajar sobre aquello que queramos 
          mejorar en nuestra vida.
          La personalidad es la tendencia estable de una persona a pensar, sentir y actuar de una determinada manera.
          <br>
          Los llamados rasgos de personalidad expresan un estilo o tendencia a la hora de procesar e interpretar 
          lo que nos ocurre, y con ello la forma en la que tendemos a sentirnos, y en consecuencia, a actuar con 
          respecto a esos acontecimientos o eventos.
        </p>
    </div>
  </div>
  
  
</template>
