<template>
  <nav class="absolute right-0 justify-end text-xl font-bold">
    <a href="/about">About</a>
    <a href="/work">Work</a>
    <a href="/resume">Resume</a>
  </nav>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style scoped>
nav{
    position: relative;
    top: 0;
    right: 0;
    display: flex;
}
</style>