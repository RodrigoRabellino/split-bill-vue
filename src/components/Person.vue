<script setup>
import { defineProps, ref } from "vue";
import { pay } from "@/store/store";
const { id, numberOfPerson, totalPerPerson, paid } = defineProps([
  "id",
  "numberOfPerson",
  "totalPerPerson",
  "paid",
]);
let paidCheck = ref(false);
const handleChange = (e) => {
  paidCheck = e.target.checked;
  pay(id);
};
</script>
<template>
  <div :class="['person', paid ? 'person__paid' : 'person__no__paid']">
    <div class="name__container">
      <h4>Person {{ numberOfPerson }}</h4>
      <div class="paid">
        <label for="check-paid">Paid </label>
        <input
          type="checkbox"
          name="check-paid"
          @change="handleChange"
          :value="paidCheck"
        />
      </div>
    </div>
    <p class="person__to__pay">
      Total:
      {{
        new Intl.NumberFormat("en-US", {
          style: "currency",
          currency: "USD",
        }).format(totalPerPerson)
      }}
    </p>
  </div>
</template>

<style scoped>
.person {
  display: flex;
  padding: 1rem;
  margin-top: 1rem;
  flex-direction: column;
  justify-content: space-between;
  height: 100px;
  width: 200px;
  border-radius: 15px;
  font-size: 20px;
  overflow: hidden;
  background-color: white;
}
.name__container {
  display: flex;
  justify-content: space-between;
  background-color: transparent;
}
.person__paid {
  transition: 0.4s;
  background-color: rgb(173, 255, 47, 0.3);
}
.person__no__paid {
  transition: 0.4s;
  background-color: rgba(153, 153, 153, 0.4);
}
.person__to__pay {
  width: 100%;
  text-align: center;
  font-weight: 600;
}
</style>
