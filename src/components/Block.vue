<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script setup>
import { onMounted, ref } from "vue";
const props = defineProps({
  delay: Number,
});
const showBlock = ref(false);
const timer = ref(null);
const reactionTimer = ref(0);

const startTimer = () => {
  timer.value = setInterval(() => {
    reactionTimer.value += 10;
  }, 10);
};
const emit = defineEmits();
const stopTimer = () => {
  clearInterval(timer);
  //   console.log(reactionTimer.value);

  emit("end", reactionTimer.value);
};

onMounted(() => {
  //   console.log("component mounted");
  setTimeout(() => {
    showBlock.value = true;
    startTimer();
    // console.log(props.delay);
  }, props.delay);
});
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  color: white;
  background: #0fafa7;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
