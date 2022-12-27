<template>
  <div class="mx-auto md:w-1/3">
    <h2 class="text-3xl">Work</h2>
    <div class="mt-5">
      <span class="font-bold">Filter: </span>
      <div>
        <button
          class="p-1 m-1 border-2 rounded hover:border-teal-300"
          :class="
            selectedCategories.includes(cat)
              ? 'border-teal-300'
              : 'border-gray-200'
          "
          @click="handleCategoryButtonClick(cat)"
          v-for="cat in categories"
          :key="cat"
        >
          {{ cat }}
        </button>
      </div>
    </div>
    <ul class="">
      <li class="my-24" v-for="project in filteredProjects" :key="project.name">
        <a
          v-if="project.href"
          :href="project.href"
          class="font-bold underline hover:text-teal-400"
          ><h2 class="text-2xl">{{ project.name }} ({{ project.date }})</h2></a
        >
        <h2 v-else class="text-2xl">{{ project.name }} ({{ project.date }})</h2>
        <p class="my-4">
          {{ project.description }}
        </p>
        <span v-if="project.embed" v-html="project.embed"></span>
        <img v-if="project.img" :src="project.img" alt="" />
      </li>
    </ul>
  </div>
</template>

<script  lang="ts">
import { defineComponent } from "vue";
// import {Project} from '@/types/Project';
export default defineComponent({
  name: "WorkView",
  data() {
    return {
      selectedCategories: [] as string [],
      categories: ["Web", "Animation", "Game", "VR"] as string [],
      projects: [
        {
          name: "Nextgen Scholarship Portal",
          date: "2021-",
          description:
            "I created a scholarship application and evaluation portal for a regional statistics society. The committee required a FERPA compliant site that would allow for the secure handling of student transcript information. The solution was comprised of a MERN-stack app built on AWS infrastructure.",
          href: "",
          categories: ["Web"],
        },
        {
          name: "Charles VR",
          date: "2017-",
          description:
            "Charles VR is a reconstruction of the coronation mass for Charles V, the last Holy Roman Emperor to be crowned by a pope. The aim of this project is to immerse users within the scenery of the mass and explore scholarly annotations describing both the built environment and the political background of the event. I constructed the experience within Unity and did most of the environmental modeling, texturing and lighting.",
          href: "",
          embed: `<video class="wp-video-shortcode" id="video-5544-1" width="100%" height="422" preload="metadata" controls="controls"><source type="video/mp4" src="https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4?_=1"><a href="https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4">https://dev-greenhouse-studios.pantheonsite.io/wp-content/uploads/2020/09/CVR-WithFade.mp4</a></video>`,
          categories: ["VR"],
        },
        {
          name: "Land Grab CT",
          date: "2020",
          description:
            "In collaboration with a team at Greenhouse Studios, I developed an engaging site exploring Connecticut's history of land grant institutions. I used Vue, Fullpage.js and Sanity.io to allow content writers to edit and revise the site content.",
          href: "www.landgrabct.org",
          categories: ["Web"],
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
          width="100%"
          height="315"
          src="https://www.youtube.com/embed/MM_9KT78VqM"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>`,
          categories: ["Animation"],
        },
        {
          name: "Diagram of Winds",
          date: "2019",
          description: `I was hired by a PhD candidate in English to construct his vision for a unique poetry reading experience. His design required a unique layout and randomization of poems. The winds interface is a circle of words representing a randomized set of poems. I implemented a custom frontend for a wordpress site using HTML/CSS and jQuery and devised a tagging system within wordpress that would allow for words or phrases within each poem to have hover-over definitions and explanations. There is also a light and dark mode toggle for the site.`,
          embed: `<iframe src="https://player.vimeo.com/video/760347834?h=a5e08bafc5&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" width="100%" height="315" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen title="Diagram of Winds Demo"></iframe>`,
          categories: ["Web"],
        },
        {
          name: "Léamh",
          date: "2018",
          description: `Working with a team of researchers in the field, I built an app for studying Early Modern Irish built using Vue and Firebase. We created valuable learning resources for the scholarly community including a primer on paleography and a verb conjugation generator. I designed a quiz framework that allows new types of quiz questions to be added easily.`,
          href: "https://leamhquiz.web.app/#/",
          img: "https://léamh.org/wp-content/uploads/2022/03/Screen-Shot-2022-03-11-at-11.21.34-AM-2.png",
          categories: ["Web"],
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
          embed: ` 
        <iframe
          src="https://player.vimeo.com/video/760002105?h=c9f62460a9&badge=0&autopause=0&player_id=0&app_id=58479/embed"
          allow="autoplay; fullscreen; picture-in-picture"
          allowfullscreen
          frameborder="0"
          style=" width: 100%; height: 315px"
        ></iframe>
    `,
          categories: ["Game"],
        },
        {
          name: "Boston Children's Hospital Interactive Wall Display",
          date: "2013-16",
          description: ` I worked with UConn's Digital Media and Design Department to design
          and implement several scenes for the Boston Children's Hospital
          Interactive Wall, which is a main feature of their lobby area. My main
          responsibilities were programming scenes' interactive features,
          managing scene content and testing/debugging. The musical grid scene
          was my original design that allowed players to trigger musical sounds
          from several different instrument types.`,
          embed: `  <iframe
        width="100%"
        height="315"
        src="https://www.youtube.com/embed/iJ3bpEtzg44"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>`,
          categories: ["Game"],
        },
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
  computed: {
    projectsByDate() {
      return this.projects.sort((a, b) => {
        return a.date > b.date ? -1 : 1;
      });
    },
    filteredProjects() {
      if (this.selectedCategories.length > 0) {
        return this.projectsByDate.filter((p) =>
          p.categories.some((c) => this.selectedCategories.includes(c))
        );
      }
      else return this.projectsByDate;
    },
  },
  methods: {
    // filterByCategory(category: string) {},
    handleCategoryButtonClick(category: string) {
      if (this.selectedCategories.includes(category)) {
        this.selectedCategories.splice(
          this.selectedCategories.indexOf(category)
        );
      } else {
        this.selectedCategories.push(category);
      }
    },
  },
});
</script>

<style lang="scss" scoped>
</style>