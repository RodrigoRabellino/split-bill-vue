<script setup>
import { defineProps } from "vue";
const props = defineProps(["title", "value"]);
</script>

<template>
  <div class="container">
    <span class="title">{{ props.title }}</span>
    <span class="value">{{
      new Intl.NumberFormat("en-US", {
        style: "currency",
        currency: "USD",
      }).format(props.value)
    }}</span>
  </div>
</template>

<style scoped>
.title {
  font-size: 25px;
  font-weight: bolder;
}
.value {
  font-size: 25px;
  color: rgb(36, 48, 14);
  font-weight: 600;
}
</style>
