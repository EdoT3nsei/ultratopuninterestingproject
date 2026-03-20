<script setup>
import { ref } from 'vue'
import SecretPage from './components/SecretPage.vue'
import StepOne from './components/StepOne.vue'

const code = ref('')
const currentPage = ref('home')
const error = ref('')

const validateCode = () => {
  // Exemple: code "1234" ouvre la page secrète
  if (code.value === '1234') {
    currentPage.value = 'secret'
    error.value = ''
  } else if (code.value === 'K4F3'){
    currentPage.value = 'step-one'
    error.value = 'Code incorrect'
  }
  {
    error.value = 'Code incorrect'
  }
}

const goHome = () => {
  currentPage.value = 'home'
  code.value = ''
  error.value = ''
}
</script>

<template>
  <div class="app-container">
    <!-- Page d'accueil -->
    <div v-if="currentPage === 'home'" class="home-page">
      <h1>🔒 Accès Sécurisé</h1>
      <p>Entrez votre code d'accès</p>
      
      <div class="code-input-container">
        <input 
          v-model="code"
          type="password"
          placeholder="Code d'accès"
          class="code-input"
          @keyup.enter="validateCode"
        />
        <button @click="validateCode" class="submit-btn">
          Valider
        </button>
      </div>
      
      <p v-if="error" class="error-message">{{ error }}</p>
      <p class="hint">Astuce: essayez 1234</p>
    </div>

    <!-- Page secrète -->
    <SecretPage v-else-if="currentPage === 'secret'" @go-home="goHome" />
    <StepOne v-else-if="currentPage === 'step-one'" @go-home="goHome" />
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.home-page {
  text-align: center;
  padding: 2rem;
  max-width: 400px;
  width: 100%;
}

.home-page h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: #646cff;
}

.home-page p {
  color: #888;
  margin-bottom: 2rem;
}

.code-input-container {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.code-input {
  flex: 1;
  padding: 0.75rem 1rem;
  font-size: 1.1rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  transition: border-color 0.3s;
}

.code-input:focus {
  outline: none;
  border-color: #646cff;
}

.submit-btn {
  padding: 0.75rem 1.5rem;
  font-size: 1.1rem;
  background-color: #646cff;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-btn:hover {
  background-color: #535bf2;
}

.error-message {
  color: #ff4444;
  margin: 0.5rem 0;
  font-weight: bold;
}

.hint {
  font-size: 0.9rem;
  color: #aaa;
  font-style: italic;
}
</style>
