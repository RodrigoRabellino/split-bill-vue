<script setup>
import { store, getGrandTotal } from "@/store/store";
import Label from "./Label.vue";
import Person from "./Person.vue";
</script>
<template>
  <div class="no__items" v-if="store.people.length === 0">Nothing to see</div>
  <div class="people__view" v-if="store.people.length > 0">
    <div class="header">
      <div>
        <Label title="Total:" :value="getGrandTotal()" />
      </div>
      <div>
        <Label title="remaining:" :value="store.params.remaining" />
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

<style lang="scss" scoped></style>
