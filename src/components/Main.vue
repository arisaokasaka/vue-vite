<script setup lang="ts">
import { ref } from 'vue';
const text = ref('');
const clickAddButton: (text: string) => void = (text) => alert(text);
</script>

<template>
  <div>
    <input v-model.string="text" type="text" />
    <button @click="clickAddButton(text)">Add</button>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
