<script setup lang="ts">
import { useColorMode } from "@vueuse/core";
import { Marquee } from "@selemondev/vue3-marquee";
import "@selemondev/vue3-marquee/dist/style.css";

interface sponsorsProps {
  image: string;
  name: string;
}

const sponsors: sponsorsProps[] = [
  {
    image: "brands/aicoco.png",
    name: "Aicoco",
  },
  {
    image: "brands/fifine.png",
    name: "Fifine",
  },
  {
    image: "brands/irobot.png",
    name: "iRobot",
  },
  {
    image: "brands/maono.png",
    name: "Maono",
  },
  {
    image: "brands/qcy.png",
    name: "QCY",
  },
  {
    image: "brands/soundpeats.png",
    name: "Soundpeats",
  },
];

const mode = useColorMode();
mode.value = "dark";
</script>

<template>
  <section
    id="sponsors"
    class="max-w-[75%] mx-auto pb-8 sm:pb-8"
  >
    <h2 class="text-lg md:text-xl text-center mb-6">Colaboraciones</h2>

    <div class="mx-auto">
      <Marquee
        class="gap-[3rem]"
        :fade="true"
        innerClassName="gap-[3rem]"
      >
        <div
          v-for="{ image, name } in sponsors"
          :key="name"
        >
          <div 
            :class="{
              'invert': mode === 'dark',
              'flex items-center opacity-75': true
            }"
          >
            <img
              class="mr-2 max-w-none max-h-6 h-6"
              :src="image"
              :alt="name"
            />
          </div>
        </div>
      </Marquee>
    </div>
  </section>
</template>
