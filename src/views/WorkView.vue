<template>
  <div>
    <h2 class="text-3xl">Work</h2>
    <ul>
      <li>
        <a href="https://leamhquiz.web.app/#/">Leamh Quiz</a>
      </li>
      <li>
        <a href="https://greenhousestudios.uconn.edu/#/projects/charles-vr"
          >Charles VR</a
        >
      </li>
      <li>
        <a href="https://landgrabct.org">Land Grab Connecticut</a>
      </li>
      <li>
        <a href="https://hartfordbound.com">Hartford Bound</a>
      </li>
      <li>
        <a href="https://www.by-our-love.com/">By Our Love</a>
      </li>
    </ul>

    <div class="w-1/2 m-12">
      <h2 class="text-2xl">Motion-sensing Media Display (2016)</h2>
      <p>
        In the Summer of 2016 I worked as a Graduate Assistant with the
        Department of Digital Media and Design to prototype a motion-sensing
        interactive installation for Diversified Media Group. We imagined this
        setup could be used in waiting areas and especially considered the needs
        of children and the elderly. I helped design and implement several
        scenes showcasing a motion-sensing interactive display.
      </p>
      <ul class="my-5">
        <li v-for="scene in dmgScenes" :key="scene.name" class="m-1">
          <strong>{{ scene.name }}</strong> - {{ scene.description }}
        </li>
      </ul>
      <div style="padding: 36.25% 0 0 0; position: relative">
        <iframe
          src="https://player.vimeo.com/video/760002105?h=c9f62460a9&badge=0&autopause=0&player_id=0&app_id=58479/embed"
          allow="autoplay; fullscreen; picture-in-picture"
          allowfullscreen
          frameborder="0"
          style="position: absolute; top: 0; left: 0; width: 100%; height: 100%"
        ></iframe>
      </div>
    </div>
    <div class="m-12">
      <div class="w-1/2 my-12">
        <h2 class="text-2xl">
          Boston Children's Hospital Interactive Wall Display (2016)
        </h2>
        <p>
          I worked with UConn's Digital Media and Design Department to design and implement interactive scenes for the Boston Children's Hospital Interactive Wall, which is a main feature of their lobby area. My main responsibilities were programming scenes' interactive features, managing scene content and testing/debugging. The musical grid scene was my original design that allowed players to trigger musical sounds from several different instrument types. 
        </p>
      </div>

      <!-- video -->
      <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/iJ3bpEtzg44"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "WorkView",
  data() {
    return {
      dmgScenes: [
        {
          name: "River Adventure",
          description:
            "I designed and implemented this scene where you can use gestures as a control for a arcade-style river rafting game. The gestures were created using the Microsoft Kinect Visual Gesture Builder software.",
        },
        {
          name: "Tweet and Repeat",
          description:
            "The game is essentially a skinned variation of the classic game Simon. I programmed all the game logic in C# for the Unity Game engine.",
        },
        {
          name: "Air Hockey",
          description:
            "Air Hockey was an interesting concept for this installation as it tested how playable our pointing-based control was. I implemented the physics setup and game logic for this game. The thing that really made this game an experience however was the sound design. I reused sound samples from freesound.org and applied effects to the sample chops that responded to the kinetics of the puck to create a very convincing audio dimension to this game.",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
</style>