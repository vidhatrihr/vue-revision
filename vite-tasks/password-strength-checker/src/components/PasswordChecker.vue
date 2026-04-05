<script setup>
import { ref, computed } from 'vue';

const password = ref('HelloMyeweio0');
const showPassword = ref(false);

const inputType = computed(() => {
  return showPassword.value ? 'text' : 'password';
});

const strength = computed(() => {
  const hasNumber = /\d/.test(password.value);

  if (password.value.length > 10 && hasNumber) return 'Strong';
  else if (password.value.length > 6) return 'Medium';
  else return 'Easy';
});
</script>

<template>
  <div class="card">
    <label>
      <input v-bind:type="inputType" v-model="password" />
    </label>

    <button @click="showPassword = !showPassword">Toggle</button>

    <div :class="strength">.</div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  gap: 1rem;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

button {
  padding: 0.5rem;
}

input {
  padding: 0.5rem;
}

.Strong {
  width: 100%;
  background-color: white;
}

.Medium {
  width: 66%;
  background-color: white;
}

.Easy {
  width: 33%;
  background-color: white;
}
</style>
