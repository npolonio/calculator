<template>
  <div class="calculator">
    <input type="text" v-model="display" disabled />

    <div class="buttons">
      <button @click="clearDisplay">C</button>
      <button @click="appendValue('/')">/</button>
      <button @click="appendValue('*')">*</button>
      <button @click="appendValue('-')">-</button>

      <button @click="appendValue('7')">7</button>
      <button @click="appendValue('8')">8</button>
      <button @click="appendValue('9')">9</button>
      <button @click="appendValue('+')">+</button>

      <button @click="appendValue('4')">4</button>
      <button @click="appendValue('5')">5</button>
      <button @click="appendValue('6')">6</button>
      <button @click="calculateResult" rowspan="2">=</button>

      <button @click="appendValue('1')">1</button>
      <button @click="appendValue('2')">2</button>
      <button @click="appendValue('3')">3</button>

      <button @click="appendValue('0')">0</button>
      <button @click="appendValue('.')">.</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const display = ref("");

function appendValue(value) {
  display.value += value;
}

function clearDisplay() {
  display.value = "";
}

function calculateResult() {
  try {
    display.value = eval(display.value);
  } catch (e) {
    display.value = "Error";
  }
}
</script>
