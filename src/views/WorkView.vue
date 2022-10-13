<template>
  <div class="">
    <h2 class="text-3xl">Work</h2>
    <ul class="">
      <li class="w-1/3 mx-auto my-24" v-for="project in projects" :key="project.name">
        <a :href="project.href" class="font-bold underline hover:text-teal-400"
          ><h2 class="text-2xl">{{ project.name }} ({{ project.date }})</h2></a
        >
        <p class="my-4">
          {{ project.description }}
        </p>
        <span v-if="project.embed" v-html="project.embed"></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "WorkView",
  data() {
    return {
      projects: [
        {
          name: "Charles VR",
          date: "2016-",
          description: "A thing that is cool",
          href: "",
          embed: `<video class="wp-video-shortcode" id="video-5544-1" width="750" height="422" preload="metadata" controls="controls"><source type="video/mp4" src="https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4?_=1"><a href="https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4">https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4</a></video>`,
        },
        {
          name: "Land Grab CT",
          date: "2020",
          description: "In collaboration with a team at Greenhouse Studios, I developed an engaging site exploring Connecticut's history of land grant institutions. I used Vue, Fullpage.js and Sanity.io",
          href: "www.landgrabct.org",
        },
        {
          name: "By Our Love",
          date: "2020",
          description: `I worked as a Producer on By Our Love. My responsibilites were
          managing production timelines and providing artistic direction and
          feedback for the animation team. In this project I realized a
          life-long dream of working on a project focused on marrying music and
          animation.`,
          href: "www.by-our-love.com",
          embed: ` <iframe
          width="560"
          height="315"
          src="https://www.youtube.com/embed/MM_9KT78VqM"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>`,
        },
        {
          name: "Léamh",
          date: "2018",
          description: `An app for studying Early Modern Irish built using Vue and firebase.`,
          href: "https://leamhquiz.web.app/#/",
        },
        {
          name: "Motion-sensing Media Display",
          date: "2016",
          description: `I worked as a Graduate Assistant with the
        Department of Digital Media and Design to prototype a motion-sensing
        interactive installation for Diversified Media Group. We imagined this
        setup could be used in waiting areas and especially considered the needs
        of children and the elderly. I helped design and implement several
        scenes showcasing a motion-sensing interactive display.`,
          href: "www.by-our-love.com",
          embed: ` <div style="padding: 36.25% 0 0 0; position: relative">
        <iframe
          src="https://player.vimeo.com/video/760002105?h=c9f62460a9&badge=0&autopause=0&player_id=0&app_id=58479/embed"
          allow="autoplay; fullscreen; picture-in-picture"
          allowfullscreen
          frameborder="0"
          style="position: absolute; top: 0; left: 0; width: 100%; height: 100%"
        ></iframe>
      </div>`,
        },
        {
          name: "Boston Children's Hospital Interactive Wall Display",
          date: '2016',
          description: ` I worked with UConn's Digital Media and Design Department to design
          and implement interactive scenes for the Boston Children's Hospital
          Interactive Wall, which is a main feature of their lobby area. My main
          responsibilities were programming scenes' interactive features,
          managing scene content and testing/debugging. The musical grid scene
          was my original design that allowed players to trigger musical sounds
          from several different instrument types.`,
          embed:`  <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/iJ3bpEtzg44"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>`
        }
      ],
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