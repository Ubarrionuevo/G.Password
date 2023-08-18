<template >
  <div class="d-flex align-items-center justify-content-center min-vh-100  bg-black ">
    <div class="flex flex-col items-center p-8 rounded-lg shadow-md w-80 text-center bg-black run ">
   
    <div class="div-principal"> 
      <div class="mb-6">
        <a href="https://github.com/Ubarrionuevo/G.Password" target="_blank" class="bg-red-500 hover:bg-gray-700 text-white font-bold py-2 px-4 custom-link">
          GitHub
      </a>
      <a href="https://twitter.com/TittoDev_" target="_blank" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded ml-4 custom-link">
        Twitter
      </a>
      </div>
      <h2 class="text-xl font-semibold mb-4 text-white mt-5">GPassword</h2>
      <p class="text-white">Random Password Generator</p>
      <button @click="generarContraseña" class=" text-white font-bold py-2 px-4  mb-4 bg-black click">
       Generator
      </button>
      <button @click="copiarContraseña" class="bg-black text-white font-bold py-2 px-4  mt-2 click ">
        Copy
      </button>
      <p  style="color: green;">Password has been copied!</p>
      <p class="text-white" >{{ contraseñaGenerada }}</p>
    </div>
     
      
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

.click{
  margin-right: 10px;
  border: 1px solid gray;
  border-radius: 30px;
}
.div-principal{
  border: 1px solid gray  ; 
  border-radius: 60px;
  padding: 100px;
  height: 440px; /* Establece una altura fija para el div principal */
  
}
.custom-link{
  text-decoration: none;
}
template{
  width: 20rem;
}
</style>

