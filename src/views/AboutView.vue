<template>
  <div class="mx-auto mb-32 md:w-1/3 about">
    <h2 class="mb-3 text-3xl">About Me</h2>
    <img class="w-2/3" src="../assets/IMG_20230616_162831.jpg" alt="" />
    <div class="my-5">
      <p>
        I am a <strong>musician</strong> turned
        <strong>programmer</strong> turned
        <strong>interactive media designer.</strong>
      </p>
      <p>
        I have a great interest in the intersections of Art, Design, Science and
        Technology. I seek to understand how technical systems can be designed
        to enable the creation of beautiful experiences with an empowering sense
        of utilty and possibility.
      </p>
      <p>
        I have created <strong>games</strong>, <strong>websites</strong>,
        <strong>applications</strong>,
        <strong>and a variety of interactive experiences, including work in
          AR/VR.</strong>
      </p>
      <p>
        I also have a passion for teaching and mentoring and have designed and
        taught a course on digital art.
      </p>
      <p>
        Some things I really like to nerd out on include trivia, comedy, jazz,
        cooking and gaming.
      </p>

    </div>

    <a class="text-lg font-bold underline hover:text-teal-400" href="./assets/TLResume082024.pdf"
      download="TomLeeResume"><span>Download my Résumé 📃</span></a>

  </div>
</template>

<script lang="ts">
export default {
  name: "AboutView",
};
</script>
<style scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  p {
    margin-top: 1em;
  }
}
</style>
