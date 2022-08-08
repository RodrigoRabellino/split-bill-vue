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
    <div class="person__number">Person {{ numberOfPerson }}</div>
    <div class="person__to_pay">
      {{
        new Intl.NumberFormat("en-US", {
          style: "currency",
          currency: "USD",
        }).format(totalPerPerson)
      }}
    </div>
    <div class="paid">
      <label for="check-paid">Paid</label>
      <input
        type="checkbox"
        name="check-paid"
        @change="handleChange"
        :value="paidCheck"
      />
    </div>
  </div>
</template>

<style scoped>
.person {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100px;
  border-radius: 15px;
  font-size: 20px;
  overflow: hidden;
}
.person__paid {
  background-color: rgb(173, 255, 47, 0.3);
}
.person__no__paid {
  background-color: rgba(153, 153, 153, 0.4);
}
</style>
