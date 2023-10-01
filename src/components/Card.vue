<script setup>
const props = defineProps({
  body: Number,
  mind: Number,
  luck: Number,
});

const formatRoll = (result) => {
  return result.toString().padStart(2, "+");
};
</script>

<template>
  <div class="card">
    <div class="stat body">{{ formatRoll(props.body) }}</div>
    <div class="stat mind">{{ formatRoll(props.mind) }}</div>
    <div class="stat luck">{{ formatRoll(props.luck) }}</div>
  </div>
</template>

<style scoped>
.card {
  border: 0.125rem solid var(--color-white);
  padding: 3rem;
  display: flex;
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
