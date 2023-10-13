<script setup>
import DieFace from "./DieFace.vue";
defineProps(["rolls"]);
</script>

<template>
  <div class="roll-card">
    <div class="node white">{{ rolls[0] + rolls[1] + rolls[2] }}</div>
    <div class="node red"><DieFace :pips="rolls[0]" /></div>
    <div class="node yellow">{{ rolls[0] + rolls[1] }}</div>
    <div class="node green"><DieFace :pips="rolls[1]" /></div>
    <div class="node cyan">{{ rolls[1] + rolls[2] }}</div>
    <div class="node blue"><DieFace :pips="rolls[2]" /></div>
    <div class="node magenta">{{ rolls[2] + rolls[0] }}</div>
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

.red,
.green,
.blue {
  font-size: 1.5rem;
}

.cyan,
.magenta,
.yellow {
  font-size: 2.25rem;
}

.white {
  font-size: 4.25rem;
}

/* Node positioning and coloring */

.red {
  left: calc(50% - calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-red);
}

.green {
  left: 50%;
  top: calc(50% - calc(var(--radius) * 2));
  border-color: var(--color-green);
}

.blue {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% + var(--radius));
  border-color: var(--color-blue);
}

.cyan {
  left: calc(50% + calc(var(--radius) * 1.732));
  top: calc(50% - var(--radius));
  border-color: var(--color-cyan);
  color: var(--color-cyan);
}

.magenta {
  left: 50%;
  top: calc(50% + calc(var(--radius) * 2));
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

/* Lines from RGB dice to the sum */

.red::after,
.green::after,
.blue::after {
  position: absolute;
  height: 0.125rem;
  width: 2.875rem;
  --translate: 2.875rem;
  content: "";
}

.red::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-red), var(--color-white));
}

.green::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-green), var(--color-white));
}

.blue::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-blue), var(--color-white));
}

/* Lines between RGB dice and CMY sums */

.cyan::before,
.cyan::after,
.magenta::before,
.magenta::after,
.yellow::before,
.yellow::after {
  position: absolute;
  height: 0.125rem;
  width: 4.875rem;
  --translate: 4.625rem;
  content: "";
}

.cyan::before {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-cyan), var(--color-blue));
}

.cyan::after {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-cyan), var(--color-green));
}

.magenta::before {
  transform: rotate(210deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-magenta), var(--color-red));
}

.magenta::after {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-magenta), var(--color-blue));
}

.yellow::before {
  transform: rotate(330deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-yellow), var(--color-green));
}

.yellow::after {
  transform: rotate(90deg) translate(var(--translate));
  background: linear-gradient(90deg, var(--color-yellow), var(--color-red));
}
</style>
