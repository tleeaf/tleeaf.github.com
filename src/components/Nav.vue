<template>
  <div>
    <div class="top-0 left-0 mt-8 hover:text-teal-500">
      <h1>TOM LEE</h1>
      <h3>CREATIVE TECHNOLOGIST</h3>
    </div>
    <nav class="text-xl font-bold">
      <a href="/about">About</a>
      <a href="/work">Work</a>
      <a href="/resume">Resume</a>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Nav",
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