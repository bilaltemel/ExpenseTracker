<template>
  <h3>Yeni işlem ekle</h3>
  <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
      <label for="text">Açıklama</label>
      <input type="text" v-model="text" id="text" placeholder="Açıklama..." />
    </div>
    <div class="form-control">
      <label for="amount">
        Miktar <br />
        (negatif - gider, pozitif - gelir)
      </label>
      <input type="text" v-model="amount" id="amount" placeholder="Miktar.." />
    </div>
    <button class="btn">Yeni İşlem Ekle</button>
  </form>
</template>
<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");

const emit = defineEmits(["transactionSubmitted"]);

const toast = useToast();

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("İki alanda dolu olmalıdır.");
    return;
  }

  const transactionData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmitted", transactionData);
  
  text.value = "";
  amount.value = "";
};
</script>
