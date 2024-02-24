<template>
  <div class="inc-exp-container">
    <h4>Gelir</h4>
    <p id="money-plus" class="money plus">+{{ income }}₺</p>
    <h4>Gider</h4>
    <p id="money-minus" class="money minus">{{ expenses }}₺</p>
  </div>
</template>
<script setup>
import { defineProps } from "vue";

const props = defineProps({
    income: {
      type: Number,
      required: true,
    },
    expenses: {
      type: Number,
      required: true,
    },
});
</script>
