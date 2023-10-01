<script setup>
const rollD6 = () => {
  return Math.ceil(Math.random() * 6);
};

const cardObject = {
  body: {
    roll: [rollD6(), rollD6()],
  },
  mind: {
    roll: [rollD6(), rollD6()],
  },
  luck: {
    roll: [rollD6(), rollD6()],
  },
};

const formatRoll = (dice) => {
  const result = `${dice.roll[0] - dice.roll[1]}`;
  return result.padStart(2, "+");
};
</script>

<template>
  <div class="card">
    <div class="body stat">{{ formatRoll(cardObject.body) }}</div>
    <div class="mind stat">{{ formatRoll(cardObject.mind) }}</div>
    <div class="luck stat">{{ formatRoll(cardObject.luck) }}</div>
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

.body.stat {
  color: var(--color-rose);
}

.body.stat::after {
  content: "\25A0";
}

.mind.stat {
  color: var(--color-azure);
}

.mind.stat::after {
  content: "\25B2";
}

.luck.stat {
  color: var(--color-chartreuse);
}

.luck.stat::after {
  content: "\25CF";
}
</style>
