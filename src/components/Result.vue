<template>
  <p>Reaction Time: {{ score }}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script setup>
import { onMounted, ref } from "vue";
const props = defineProps({
  score: Number,
});
const rank = ref(null);

onMounted(() => {
  if (props.score < 250) {
    rank.value = "Ninja Fingers";
  } else if (props.score < 400) {
    rank.value = "Rapid Reflexex";
  } else {
    rank.value = "Snail pace...";
  }
});
</script>
<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
