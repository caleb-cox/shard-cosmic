<script setup>
import { ref } from "vue";
import RollCard from "./components/RollCard.vue";

const rolls = ref([]);

const resetRollCard = () => {
  const roll = () => {
    return Math.ceil(Math.random() * 6);
  };

  rolls.value = [roll(), roll(), roll()];
};

resetRollCard();
</script>

<template>
  <h1>Shard Cosmic</h1>
  <RollCard :rolls="rolls" @click="resetRollCard()" />
</template>

<style scoped>
h1 {
  margin: 0 0 1rem 1rem;
}
</style>
