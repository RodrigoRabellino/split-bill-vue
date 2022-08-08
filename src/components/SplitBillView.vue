<script setup>
import InputForm from "./InputForm.vue";
import PeopleView from "./PeopleView.vue";
</script>

<template>
  <div class="container">
    <H1>Split Bill</H1>
    <div>
      <InputForm />
      <PeopleView />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.container h1 {
  font-weight: 500;
}
.container div {
  display: flex;
  padding: 1rem;
  width: 100%;
  justify-content: space-between;
}
</style>
