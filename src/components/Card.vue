<script setup>
defineProps(["rolls"]);
defineEmits(["deleteCard"]);

const signNumber = (number) => {
  return number.toString().padStart(2, "+");
};
</script>

<template>
  <div class="card">
    <div class="node red">{{ rolls[0] }}</div>
    <div class="node yellow">{{ signNumber(rolls[2] - rolls[0]) }}</div>
    <div class="node green">{{ rolls[2] }}</div>
    <div class="node cyan">{{ signNumber(rolls[1] - rolls[2]) }}</div>
    <div class="node blue">{{ rolls[1] }}</div>
    <div class="node magenta">{{ signNumber(rolls[0] - rolls[1]) }}</div>
    <div class="node white">{{ rolls[0] + rolls[1] + rolls[2] }}</div>
  </div>
</template>

<style scoped>
.card {
  cursor: pointer;
  user-select: none;
  border: 0.25rem solid var(--color-white);
  border-radius: 1rem;
  height: 24rem;
  width: 24rem;
  position: relative;
  --radius: 4rem;
}

.node {
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

.red,
.green,
.blue {
  font-size: 1.25em;
}

.yellow,
.magenta,
.cyan {
  font-size: 2em;
}

.white {
  font-size: 4em;
}

.red {
  left: 50%;
  top: calc(50% - calc(var(--radius) * 2));
  border-color: var(--color-red);
  color: var(--color-red);
}

.green {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-green);
  color: var(--color-green);
}

.blue {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-blue);
  color: var(--color-blue);
}

.cyan {
  left: 50%;
  top: calc(50% + calc(var(--radius) * 2));
  border-color: var(--color-cyan);
  color: var(--color-cyan);
}

.magenta {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-magenta);
  color: var(--color-magenta);
}

.yellow {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-yellow);
  color: var(--color-yellow);
}

.white {
  left: 50%;
  top: 50%;
  border-color: var(--color-white);
  color: var(--color-white);
}

.red::after,
.green::after,
.blue::after {
  position: absolute;
  height: 0.125rem;
  width: 2.875rem;
  --translate: 2.625rem;
  content: "";
}

.red::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-red), var(--color-white));
}

.green::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-green), var(--color-white));
}

.blue::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-blue), var(--color-white));
}

.cyan::before,
.cyan::after,
.magenta::before,
.magenta::after,
.yellow::before,
.yellow::after {
  position: absolute;
  height: 0.125rem;
  width: 4.875rem;
  --translate: 4.375rem;
  content: "";
}

.cyan::before {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-cyan), var(--color-green));
}

.cyan::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-cyan), var(--color-blue));
}

.magenta::before {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-magenta), var(--color-blue));
}

.magenta::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-magenta), var(--color-red));
}

.yellow::before {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-yellow), var(--color-red));
}

.yellow::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-yellow), var(--color-green));
}
</style>
