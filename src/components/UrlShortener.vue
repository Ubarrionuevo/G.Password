<template>
  <div class="d-flex align-items-center justify-content-center min-vh-100 bg-black">
    <div class="flex flex-col items-center p-4 rounded-lg shadow-md w-90 text-center bg-black run">
      <div class="mb-4">
        <a href="https://github.com/Ubarrionuevo/G.Password" target="_blank" class="bg-red-500 hover:bg-gray-700 text-white font-bold py-2 px-4 custom-link">
          GitHub
        </a>
        <a href="https://twitter.com/TittoDev_" target="_blank" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 ml-4 custom-link">
          Twitter
        </a>
      </div>
      <h2 class="text-xl font-semibold mb-2 text-white mt-5">GPassword</h2>
      <p class="text-white">Random Password Generator</p>
      <button @click="generarContraseña" class="text-white font-bold py-2 px-4 mb-2 bg-black click">
        Generator
      </button>
      <button @click="copiarContraseña" class="bg-black text-white font-bold py-2 px-4 click">
        Copy
      </button>
      <p class="text-white">{{ contraseñaGenerada }}</p>
      <h6 v-if="copied" style="color: green;">Password copied successfully!</h6>
    </div>
  </div>
</template>
<!-- 
<template>
  <div class="d-flex align-items-center justify-content-center min-vh-100 bg-black">
    <div class="flex flex-col items-center p-4 rounded-lg shadow-md w-90 text-center bg-black run">
      <div class="mb-4">
        <a href="https://github.com/Ubarrionuevo/G.Password" target="_blank" class="bg-red-500 hover:bg-gray-700 text-white font-bold py-2 px-4 custom-link">
          GitHub
        </a>
        <a href="https://twitter.com/TittoDev_" target="_blank" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 ml-4 custom-link">
          Twitter
        </a>
      </div>
      <h2 class="text-xl font-semibold mb-2 text-white mt-5">GPassword</h2>
      <p class="text-white">Random Password Generator</p>
      <button @click="generarContraseña" class="text-white font-bold py-2 px-4 mb-2 bg-black click">
        Generator
      </button>
      <button @click="copiarContraseña" class="bg-black text-white font-bold py-2 px-4 click">
        Copy
      </button>
      <p class="text-white">{{ contraseñaGenerada }}</p>
      <h6 v-if="copied" style="color: green;">Password copied successfully!</h6>
    </div>
  </div>
</template> -->

<!-- Resto del código -->




<script>
import cryptoRandomString from 'crypto-random-string';

export default {
  data() {
    return {
      contraseñaGenerada: '',
      copied: false,
     
        
    };
  },
  methods: {
    generarContraseña() {
      const length = 16; // Longitud de la contraseña
    const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()_+{}|:<>?~-'; // Caracteres posibles
    const contraseña = cryptoRandomString({ length, characters });
  
    this.contraseñaGenerada = contraseña;
    this.copied = false;
  },
    
  

    copiarContraseña() {
     const textarea = document.createElement('textarea');
       textarea.value = this.contraseñaGenerada;
       document.body.appendChild(textarea);
      textarea.select();
     document.execCommand('copy');
      document.body.removeChild(textarea);
      this.copied = true;
   
      }}}
</script>

<style>

.click{
  margin-right: 10px;
  border: 1px solid gray;
  border-radius: 30px;
}

.custom-link{

  text-decoration: none;
}
template{
  width: 20rem;
}
</style>

