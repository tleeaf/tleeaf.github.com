<template>
  <span>
    <span class="flex gap-1"
      ><a href="https://github.com/tleeaf"
        ><div
          class="w-10 h-10 github hover:bg-teal-400 hover:scale-125"
        ></div
      ></a>
      <a href="https://www.instagram.com/teeleeaf/"
        ><div class="w-10 h-10 ig hover:scale-125"></div
      ></a>
      <a href="mailto:jcblee@gmail.com"
        ><div class="w-10 h-10 mail hover:scale-125"></div
      ></a>
    </span>
  </span>
</template>

<script lang="ts">
export default {};
</script>

<style scoped>
@import 'material-icons/iconfont/material-icons.scss';
.github{
  background-color: black;
  -webkit-mask: url('../assets/icons8-github.svg') no-repeat center;
  mask: url('../assets/icons8-github.svg') no-repeat center;
}
.ig{
  background-color: black;
  -webkit-mask: url('../assets/icons8-instagram.svg') no-repeat center;
  mask: url('../assets/icons8-instagram.svg') no-repeat center;
}
.mail{
  background-color: black;
  -webkit-mask: url('../assets/icons8-circled-envelope-30.png') no-repeat center;
  mask: url('../assets/icons8-circled-envelope-30.png') no-repeat center;
}
div:hover{
  background-color: #88EEEE;
  transition:ease-in-out 0.3s;
}
</style>