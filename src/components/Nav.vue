<template>
  <div>
    <div class="top-0 left-0 mt-8 hover:text-teal-500">
      <h1>TOM LEE</h1>
      <h3>CREATIVE TECHNOLOGIST</h3>
    </div>
    <socials></socials>
    <nav class="text-xl font-bold">
      <a href="/#/about">About</a>
      <a href="/#/work">Work</a>
      <!-- <a href="/#/resume">Resume</a> -->
    </nav>
  </div>
</template>

<script lang="ts">
import Socials from './Socials.vue'
export default {
    name: "Nav",
    components: { Socials }
};
</script>

<style scoped>
nav {
  position: relative;
  top: 0;
  right: 0;
  display: flex;
}
</style>