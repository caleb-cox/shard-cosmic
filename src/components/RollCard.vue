<script setup>
import DieFace from "./DieFace.vue";
defineProps(["rolls"]);
</script>

<template>
  <div class="roll-card">
    <div class="node white">{{ rolls[0] + rolls[1] + rolls[2] }}</div>
    <div class="node magenta"><DieFace :pips="rolls[0]" /></div>
    <div class="node red">{{ rolls[0] + rolls[1] }}</div>
    <div class="node yellow"><DieFace :pips="rolls[1]" /></div>
    <div class="node green">{{ rolls[1] + rolls[2] }}</div>
    <div class="node cyan"><DieFace :pips="rolls[2]" /></div>
    <div class="node blue">{{ rolls[2] + rolls[0] }}</div>
  </div>
</template>

<style scoped>
.roll-card {
  cursor: pointer;
  user-select: none;
  border: 0.25rem solid var(--color-white);
  border-radius: 1rem;
  height: 25rem;
  width: 25rem;
  position: relative;
  --radius: 4.25rem;
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

/* Node sizing */

.white {
  font-size: 4.25rem;
}

.red,
.green,
.blue {
  font-size: 2.25rem;
}

.cyan,
.magenta,
.yellow {
  font-size: 1.5rem;
}

/* Node positioning and coloring */

.white {
  left: 50%;
  top: 50%;
  border-color: var(--color-white);
  color: var(--color-white);
}

.red {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-red);
  color: var(--color-red);
}

.green {
  left: 50%;
  top: calc(50% + calc(var(--radius) * 2));
  border-color: var(--color-green);
  color: var(--color-green);
}

.blue {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-blue);
  color: var(--color-blue);
}

.cyan {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-cyan);
}

.magenta {
  left: 50%;
  top: calc(50% - calc(var(--radius) * 2));
  border-color: var(--color-magenta);
}

.yellow {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-yellow);
}

/* Lines between RGB sums and CMY dice */

.red::before,
.red::after,
.green::before,
.green::after,
.blue::before,
.blue::after {
  position: absolute;
  height: 0.125rem;
  width: 4.875rem;
  --translate: 4.625rem;
  content: "";
}

.red::before {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-red), var(--color-magenta));
}

.red::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-red), var(--color-yellow));
}

.green::before {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-green), var(--color-yellow));
}

.green::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-green), var(--color-cyan));
}

.blue::before {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-blue), var(--color-cyan));
}

.blue::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-blue), var(--color-magenta));
}

/* Lines from CMY dice to the sum */

.cyan::after,
.magenta::after,
.yellow::after {
  position: absolute;
  height: 0.125rem;
  width: 2.875rem;
  --translate: 2.875rem;
  content: "";
}

.cyan::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-cyan), var(--color-white));
}

.magenta::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-magenta), var(--color-white));
}
.yellow::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-yellow), var(--color-white));
}
</style>
