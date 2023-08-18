<template >
  <div class="d-flex align-items-center justify-content-center min-vh-100  bg-black ">
    <div class="flex flex-col items-center p-8 rounded-lg shadow-md w-80 text-center bg-black w-full ">
      <div class="mb-6">
        <a href="https://github.com/tu-usuario/tu-proyecto" target="_blank" class="bg-red-500 hover:bg-gray-700 text-white font-bold py-2 px-4 custom-link">
          GitHub
      </a>
      <a href="https://twitter.com/TittoDev_" target="_blank" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded ml-4 custom-link">
        Twitter
      </a>
      </div>
    
      <h2 class="text-xl font-semibold mb-4 text-white ">GPassword</h2>
      <p class="text-white">Random Password Generator</p>
      <button @click="generarContraseña" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mb-4 bg-black">
       Generator
      </button>
      <button @click="copiarContraseña" class="bg-black hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-2">
        Copy
      </button>
      <p class="text-white" v-if="contraseñaGenerada">{{ contraseñaGenerada }}</p>
      
    </div>

  </div>
 
</template>

<script>
export default {
  data() {
    return {
      contraseñaGenerada: ''
    };
  },
  methods: {
    generarContraseña() {
      const caracteres = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()_+{}|:<>?~-';
      const longitudMinima = 16;
      let contraseña = '';

      while (contraseña.length < longitudMinima) {
        const randomIndex = Math.floor(Math.random() * caracteres.length);
        contraseña += caracteres.charAt(randomIndex);
      }

      this.contraseñaGenerada = contraseña;
    },

    copiarContraseña() {
      const textarea = document.createElement('textarea');
      textarea.value = this.contraseñaGenerada;
      document.body.appendChild(textarea);
      textarea.select();
      document.execCommand('copy');
      document.body.removeChild(textarea);
      
    }
  }
};
</script>

<style>
.custom-link{
  text-decoration: none;
}
template{
  width: 20rem;
}
</style>

