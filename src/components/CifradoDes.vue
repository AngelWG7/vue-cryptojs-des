<template>
  <div class="crypto-container">
    <div class="crypto-card">
      <h2 class="crypto-title">Cifrado y Descifrado DES</h2>
      <label for="text" class="crypto-label">Texto:</label>
      <input v-model="inputText" id="text" class="crypto-input" type="text" />
      <br />
      <button @click="encryptText" class="crypto-button crypto-encrypt-button">Cifrar</button>
      <button @click="decryptText" class="crypto-button crypto-decrypt-button">Descifrar</button>
      <br />
      <label for="result" class="crypto-label">Resultado:</label>
      <input v-model="resultText" id="result" class="crypto-input" type="text" />
    </div>
  </div>
</template>
  
<script>
import CryptoJS from "crypto-js";

export default {
  data() {
    return {
      inputText: "",
      resultText: "",
      key: "miClave1", // Clave de cifrado DES (debe ser de 8 caracteres)
    };
  },
  methods: {
    encryptText() {
      // Cifrado DES
      const encrypted = CryptoJS.DES.encrypt(this.inputText, this.key);

      // Establece el texto cifrado en la variable de resultados
      this.resultText = encrypted.toString();
    },
    decryptText() {
      // Descifrado DES
      const decrypted = CryptoJS.DES.decrypt(this.resultText, this.key);

      // Convierte el texto descifrado en una cadena legible
      this.resultText = decrypted.toString(CryptoJS.enc.Utf8);
    },
  },
};
</script>
  
<style>
.crypto-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f5f5f5;
}

.crypto-card {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  width: 400px;
  text-align: center;
}

.crypto-title {
  font-family: 'Arial', sans-serif;
  font-size: 24px;
  margin-bottom: 20px;
}

.crypto-label {
  font-family: 'Arial', sans-serif;
  font-size: 16px;
}

.crypto-input {
  width: 350px;
  padding: 5px;
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  margin-top: 5px;
  margin-right: 10;
  margin-bottom: 15px;
}

.crypto-button {
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  cursor: pointer;
  margin-bottom: 10px;
  transition: background-color 0.3s;
}

.crypto-button:hover {
  background-color: #0056b3;
}

.crypto-encrypt-button {
  margin-right: 10px;
}
</style>
  