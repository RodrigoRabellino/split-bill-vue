<script setup>
import { store, getGrandTotal } from "@/store/store";
import Label from "./Label.vue";
import Person from "./Person.vue";
</script>
<template>
  <div class="no__items" v-if="store.people.length === 0">Nothing to see</div>
  <div class="people__view" v-if="store.people.length > 0">
    <div class="header">
      <div class="total__container">
        <Label title="Total:" :value="getGrandTotal()" />
        <Label title="Remaining:" :value="store.params.remaining" />
      </div>
    </div>
    <div class="people__container">
      <Person
        v-for="person in store.people"
        :key="person.id"
        :id="person.id"
        :numberOfPerson="person.numberOfPerson"
        :totalPerPerson="person.totalPerPerson"
        :paid="person.paid"
      />
    </div>
  </div>
</template>

<style scoped>
.total__container {
  padding: 1rem;
}
.people__container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 1rem;
  grid-auto-rows: minmax(100px, auto);
}
</style>
