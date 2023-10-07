<script setup>
defineProps(["rolls"]);

defineEmits(["deleteCard"]);
</script>

<template>
  <div class="card">
    <div class="stat red">{{ rolls[0] }}</div>
    <div class="stat yellow">{{ rolls[0] + rolls[1] }}</div>
    <div class="stat green">{{ rolls[1] }}</div>
    <div class="stat cyan">{{ rolls[1] + rolls[2] }}</div>
    <div class="stat blue">{{ rolls[2] }}</div>
    <div class="stat magenta">{{ rolls[0] + rolls[2] }}</div>
    <div class="stat white">{{ rolls[0] + rolls[1] + rolls[2] }}</div>
  </div>
</template>

<style scoped>
.card {
  cursor: pointer;
  border: 0.25rem solid var(--color-white);
  height: 24rem;
  width: 24rem;
  position: relative;
  --radius: 4rem;
}

.stat {
  position: absolute;
  transform: translate(-50%, -50%);
  border: 0.125rem solid var(--color-white);
  border-radius: 50%;
  width: 2em;
  height: 2em;
  display: flex;
  align-items: center;
  justify-content: center;
}

.red {
  left: 50%;
  top: calc(50% - calc(var(--radius) * 2));
  border-color: var(--color-red);
  color: var(--color-red);
}

.yellow {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-yellow);
  color: var(--color-yellow);
  font-size: 2rem;
}

.green {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-green);
  color: var(--color-green);
}

.cyan {
  left: 50%;
  top: calc(50% + calc(var(--radius) * 2));
  border-color: var(--color-cyan);
  color: var(--color-cyan);
  font-size: 2rem;
}

.blue {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-blue);
  color: var(--color-blue);
}

.magenta {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-magenta);
  color: var(--color-magenta);
  font-size: 2rem;
}

.white {
  left: 50%;
  top: 50%;
  font-size: 4rem;
}
</style>
