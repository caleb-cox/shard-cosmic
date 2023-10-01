<script setup>
import Card from "./components/Card.vue";
</script>

<template>
  <div class="hand">
    <Card v-for="_ in 10" />
  </div>
</template>

<style scoped>
.hand {
  display: flex;
  justify-content: center;
  gap: 4rem;
  flex-wrap: wrap;
}
</style>
