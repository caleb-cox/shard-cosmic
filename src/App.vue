<script setup>
import { ref } from "vue";
import Card from "./components/Card.vue";

const cards = ref({});

const addCard = () => {
  const roll = () => {
    const d1 = Math.ceil(Math.random() * 6);
    const d2 = Math.ceil(Math.random() * 6);
    return d1 - d2;
  };

  cards.value[crypto.randomUUID()] = {
    body: roll(),
    mind: roll(),
    luck: roll(),
  };
};

const deleteCard = (uuid) => {
  delete cards.value[uuid];
};
</script>

<template>
  <div class="app">
    <div class="hand">
      <Card
        v-for="(card, uuid) in cards"
        :body="card.body"
        :mind="card.mind"
        :luck="card.luck"
        @delete-card="deleteCard(uuid)"
      />
    </div>
    <button @click="addCard()">Add Card</button>
  </div>
</template>

<style scoped>
button {
  height: 3rem;
  width: 12.5rem;
}

.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3rem;
}

.hand {
  border: 0.125rem solid var(--color-white);
  padding: 2rem;
  min-height: calc(0.125rem + 2rem + 17.5rem + 2rem + 0.125rem);
  min-width: calc(0.125rem + 2rem + 12.5rem + 2rem + 0.125rem);
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}
</style>
