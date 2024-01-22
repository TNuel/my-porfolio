<script setup lang="ts">
import { ref } from "vue";
import AboutLink from "./AboutLink.vue";

const date = ref("");

const year = ref<number>(1994);
const month = ref<number>(4);
const day = ref<number>(16);
const age = ref<number | null>(null);

const calculateAge = () => {
  const today = new Date();
  const birthDate = new Date(year.value, month.value - 1, day.value);

  const yearsDiff = today.getFullYear() - birthDate.getFullYear();
  const isMonthBeforeBirthMonth = today.getMonth() < birthDate.getMonth(); 
  const isMonthAndDayBeforeBirthMonthAndDay = today.getMonth() === birthDate.getMonth() && today.getDate() < birthDate.getDate();
  
  if (isMonthBeforeBirthMonth || isMonthAndDayBeforeBirthMonthAndDay) {
    age.value = yearsDiff - 1;
    console.log(age.value);
  } else {
    age.value = yearsDiff;
    console.log(age.value);
  }
};

calculateAge();

const links = [
  {
    label: "Github",
    url: "https://github.com/TNuel",
    description: "a code hosting platform for version control and collaboration",
    iconPath: "/icons/about/github.svg"
  },
  {
    label: "LinkedIn",
    url: "https://www.linkedin.com/in/tolani-emmanuel-a360b7131/",
    description: "a business and employment-oriented online service",
    iconPath: "/icons/about/linkedin.svg"
  },
  {
    label: "Twitter",
    url: "https://twitter.com/NuelTolani",
    description: "a free social networking site where users broadcast short posts known as tweets",
    iconPath: "/icons/about/twitter.svg"
  },
  // {
  //   label: "Letterboxd",
  //   url: "https://letterboxd.com/Akasiek/",
  //   description: "a social networking service for sharing and discussing films",
  //   iconPath: "/icons/about/letterboxd.svg"
  // },
  // {
  //   label: "Literal.club",
  //   url: "https://literal.club/akasiek",
  //   description: "a social networking service for sharing and discussing books",
  //   iconPath: "/icons/about/literal-club.svg"
  // }
];
</script>

<template>
  <section class="bg-primary-light w-screen h-screen flex flex-col justify-center px-4 sm:px-6 md:px-12 2xl:px-24">
    <div class="max-w-3xl">
      <h1 class="slide-title">Something about me</h1>
      <div class="flex flex-col gap-3 lg:gap-5 text-primary-gray text-base lg:text-lg">
        <p>Like I said my name is Emmanuel. I'm a <b>Mid-level Frontend Developer</b> located in Ibadan, Nigeria.</p>
        <p>I started my coding adventure 4th of June, 2020. First it was <i>HTML, CSS, Tailwind CSS, Javascript</i> and then it just went on to Javascript framework like Jquery, React and Vue.js etc</p>
        <p>
          Music and Food are a big part of me. I love good music and in particular the genres of <b>Hip-Hop</b> and <b>Afro-Beat</b>.
        </p>
        <div>
          <p>Finding me on other socials is easy. Just look here:</p>
          <section class="flex gap-4 sm:gap-6 lg:gap-10 grid-cols-5 w-full mt-4">
            <template v-for="(link, index) in links" :key="index">
              <AboutLink :link="link" />
            </template>
          </section>
        </div>
      </div>
    </div>
  </section>
</template>
