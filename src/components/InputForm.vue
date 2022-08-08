<script setup>
import { ref } from "vue";
import { store, calculate } from "@/store/store";

const total = ref(0);
const tip = ref(0);
const people = ref(0);

const handleSubmit = () => {
  store.params.total = total;
  store.params.tip = tip;
  store.params.people = people;
  calculate();
};
</script>
<template>
  <form action="" @submit.prevent="handleSubmit">
    <div class="form__container">
      <div class="input__container">
        <label for="total"> Total </label>
        <input type="number" name="total" required v-model="total" />
      </div>
      <div class="input__container">
        <label for="tip"> Tip % </label>
        <input type="number" name="tip" required v-model="tip" />
      </div>
      <div class="input__container">
        <label for="people"> Total People</label>
        <input type="number" name="people" required v-model="people" />
      </div>
      <div>
        <input type="submit" value="calculate" class="btn" />
      </div>
    </div>
  </form>
</template>

<style scoped>
.input__container {
  text-align: center;
  font-weight: 500;
  display: flex;
  flex-direction: column;
  padding: 0.65rem 0;
}
.input__container input {
  font-size: 15px;
  text-align: center;
  border: none;
  border-radius: 50px;
  padding: 0.65rem;
  padding-left: 1rem;
  background-color: white;
  -webkit-appearance: none;
}
.input__container input:focus-visible {
  border: none;
  outline: none;
  -webkit-appearance: none;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

.btn {
  transition: 0.4s;
  width: 100%;
  background-color: violet;
  border: 1px solid violet;
  border-radius: 50px;
  padding: 0.65rem;
  font-size: 15px;
  font-weight: 500;
  color: #fff;
  text-transform: uppercase;
}
.btn:hover {
  transition: 0.4s;
  background-color: rgb(238, 130, 238, 0.2);
  color: violet;
}
</style>
