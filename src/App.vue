<script setup>
import { ref } from "vue";
import Card from "./components/Card.vue";

const roll = () => {
  const d1 = Math.ceil(Math.random() * 6);
  const d2 = Math.ceil(Math.random() * 6);
  return d1 - d2;
};

const cards = ref([
  {
    body: roll(),
    mind: roll(),
    luck: roll(),
  },
]);
</script>

<template>
  <div class="hand">
    <Card
      v-for="card in cards"
      :body="card.body"
      :mind="card.mind"
      :luck="card.luck"
    />
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
