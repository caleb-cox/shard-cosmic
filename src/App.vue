<script setup>
import { ref } from "vue";
import Card from "./components/Card.vue";

const rolls = ref([]);

const resetCard = () => {
  const roll = () => {
    return Math.ceil(Math.random() * 6);
  };

  rolls.value = [roll(), roll(), roll()];
};

resetCard();
</script>

<template>
  <h1>Shard Cosmic</h1>
  <Card :rolls="rolls" @click="resetCard()" />
</template>

<style scoped>
h1 {
  margin-bottom: 1rem;
}
</style>
