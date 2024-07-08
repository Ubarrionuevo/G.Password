<template id="form"> 
  <div class="d-flex align-items-center justify-content-center min-vh-100 bg-black">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-8">
          <div class="card bg-black text-white shadow-lg">
            <div class="card-body">
              <div class="text-center mb-4">
                <a href="https://github.com/Ubarrionuevo/G.Password" target="_blank" class="btn btn-link text-danger font-bold">
                  GitHub
                </a>
                <a href="https://twitter.com/TittoDev_" target="_blank" class="btn btn-link text-primary font-bold">
                  Twitter
                </a>
              </div>
              <h2 class="text-xl font-semibold mb-4 text-center">GPassword</h2>
              <p class="text-white text-center">Password Generator</p>
              <div class="d-flex justify-content-center mb-3">
                <button @click="generarContraseña" class="btn btn-dark text-white font-bold py-2 px-4 mr-2">
                  Generate
                </button>
                <button @click="copiarContraseña" class="btn btn-dark text-white font-bold py-2 px-4">
                  Copy
                </button>
              </div>
              <div class="text-center">
                <div class="password-container mb-3">
                  <p class="text-white">{{ contraseñaGenerada }}</p>
                </div>
                <h6 class="text-success mb-0 position-absolute start-50 translate-middle-x" v-if="copied">Password copied successfully!</h6>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

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
    }
  }
}
</script>

<style>
.password-container {
  position: relative;
}

.password-container p {
  margin-bottom: 0; /* Evita el espacio debajo del texto de la contraseña */
}

.text-success {
  bottom: 10px; /* Ajuste fino de la posición vertical */
}
</style>
