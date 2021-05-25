<template>
  <Navigation />
  <div class="flex">
    <div class="container">
      <router-view />
    </div>
  </div>
</template>

<script>
import Navigation from "@/components/Navigation";

export default {
  components: {
    Navigation,
  },
};
</script>

<style>
</style>
