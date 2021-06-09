<template>
  <div class="container mx-auto">
    <div class="w-full md:w-5/6 mx-auto md:mt-10">
      <Articles />
    </div>
  </div>
</template>

<script setup>
import Articles from "./components/Articles.vue";
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap");
body {
  font-family: "Inter", sans-serif !important;
}
</style>
