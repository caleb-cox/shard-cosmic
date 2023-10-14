<script setup>
defineProps(["pips"]);
</script>

<template>
  <div class="face">
    <div v-for="_ in pips" class="pip"></div>
  </div>
</template>

<style scoped>
.face {
  display: grid;
  gap: 0.125em;
  grid-template-columns: repeat(3, 0.25em);
  grid-template-rows: repeat(3, 0.25em);
  grid-template-areas:
    "a . c"
    "e g f"
    "d . b";
}

.pip {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

.pip:nth-child(2) {
  grid-area: b;
}

.pip:nth-child(3) {
  grid-area: c;
}

.pip:nth-child(4) {
  grid-area: d;
}

.pip:nth-child(5) {
  grid-area: e;
}

.pip:nth-child(6) {
  grid-area: f;
}

.pip:nth-child(odd):last-child {
  grid-area: g;
}

.red .pip {
  background-color: var(--color-red);
}

.green .pip {
  background-color: var(--color-green);
}

.blue .pip {
  background-color: var(--color-blue);
}
</style>
