<script setup>
defineProps(['onGoHome'])
defineEmits(['go-home'])
</script>

<template>
  <div class="secret-page">
    <div class="content">
      <h1>✨ Bienvenue à l'étape 1</h1>
      <p>Vous avez entré le bon code.</p>
      
      <div class="secret-content">
        <h2>Pour accéder à la prochaine étape :</h2>
        <p>Envoyez "Saucisse" à votre bien-aimé.</p>
        <p>Tip : Pensez à noter vos codes quelque part afin de mieux retrouver les éventuellesinformations dont vous aurez besoin plus tard.</p>
      </div>

      <button @click="$emit('go-home')" class="back-btn">
        ← Retour à l'accueil
      </button>
    </div>
  </div>
</template>

<style scoped>
.secret-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  padding: 2rem;
}

.content {
  text-align: center;
  max-width: 600px;
}

.content h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.content > p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.secret-content {
  background: rgba(255, 255, 255, 0.1);
  padding: 2rem;
  border-radius: 12px;
  margin: 2rem 0;
  backdrop-filter: blur(10px);
}

.secret-content h2 {
  margin-bottom: 1rem;
}

.secret-content p {
  margin: 0.5rem 0;
  opacity: 0.9;
}

.back-btn {
  margin-top: 2rem;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  background-color: rgba(255, 255, 255, 0.2);
  color: white;
  border: 2px solid white;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s;
}

.back-btn:hover {
  background-color: rgba(255, 255, 255, 0.3);
  transform: translateY(-2px);
}
</style>
