<script setup>
defineProps(["body", "mind", "luck"]);

defineEmits(["deleteCard"]);

const formatRoll = (result) => {
  return result.toString().padStart(2, "+");
};
</script>

<template>
  <div class="card" @click="$emit('deleteCard')">
    <div class="stat body">{{ formatRoll(body) }}</div>
    <div class="stat mind">{{ formatRoll(mind) }}</div>
    <div class="stat luck">{{ formatRoll(luck) }}</div>
  </div>
</template>

<style scoped>
.card {
  cursor: pointer;
  border: 0.125rem solid var(--color-white);
  height: 17.5rem;
  width: 12.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 1rem;
}

.stat {
  font-size: 3rem;
  line-height: 1;
}

.stat::after {
  margin-left: 1rem;
}

.body {
  color: var(--color-rose);
}

.body::after {
  content: "\25A0";
}

.mind {
  color: var(--color-azure);
}

.mind::after {
  content: "\25B2";
}

.luck {
  color: var(--color-chartreuse);
}

.luck::after {
  content: "\25CF";
}
</style>
