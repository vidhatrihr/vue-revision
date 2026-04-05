<script setup>
import { reactive, computed } from 'vue';

const character = reactive({
  name: 'vidu',
  role: 'role',
  level: 1,
  bio: 'I am a superhero',
});

const levelTitle = computed(() => {
  if (character.level >= 1 && character.level <= 10) return 'Novice';
  else if (character.level >= 11 && character.level <= 30) return 'Adventurer';
  else if (character.level >= 31 && character.level <= 60) return 'Veteran';
  else return 'Legend';
});
</script>

<template>
  <h2>{{ levelTitle }}</h2>
  <div class="input-card">
    <label>
      Name:
      <input type="text" v-model="character.name" />
    </label>

    <label>
      Role:
      <input type="text" v-model="character.role" />
    </label>

    <label>
      Level:
      <input type="number" v-model="character.level" />
    </label>

    <label>
      Bio:
      <textarea v-model="character.bio"></textarea>
    </label>
  </div>

  <div class="preview-card">
    <p>Name: {{ character.name }}</p>
    <p>Role: {{ character.role }}</p>
    <p>Level: {{ character.level }}</p>
    <p>Bio: {{ character.bio }}</p>
  </div>
</template>

<style scoped>
.input-card {
  display: flex;
  gap: 1rem;
  align-items: center;
}

input,
textarea {
  padding: 0.25rem;
  font-size: 1rem;
}

.preview-card {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
  font-size: 1.5rem;
}
</style>
