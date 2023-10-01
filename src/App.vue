<template>
  <div class="wrapper">
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :score="score" />
  </div>
</template>

<script setup>
// import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
import { ref } from "vue";

const isPlaying = ref(false);
const delay = ref(null);
const score = ref(null);
const showResult = ref(false);

const start = () => {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
  showResult.value = false;
};

const endGame = (reactionTime) => {
  score.value = reactionTime;
  isPlaying.value = false;
  showResult.value = true;
};
</script>

<style scoped>
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-style: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
