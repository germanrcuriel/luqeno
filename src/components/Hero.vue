<script setup lang="ts">
import { ArrowRight } from "lucide-vue-next";
import { Button } from "@/components/ui/button";
</script>

<template>
  <section class="container">
    <div
      class="grid place-items-center lg:max-w-screen-xl gap-8 mx-auto py-16 md:py-16"
    >
      <div class="text-center space-y-8">
        <div
          class="max-w-screen-md mx-auto text-center text-5xl md:text-6xl font-bold"
        >
          <h1>
            <span
              class="text-transparent bg-gradient-to-r from-primary to-[#D247BF] bg-clip-text"
              >
              Tech
            </span>
            and
            <span
              class="text-transparent bg-gradient-to-r from-[#D247BF] to-primary bg-clip-text"
              >Lifestyle
            </span>
          </h1>
        </div>

        <div class="space-y-4 md:space-y-0 md:space-x-4">
          <Button class="w-5/6 md:w-1/4 font-bold group/arrow">
            Enlaces
            <ArrowRight
              class="size-5 ml-2 group-hover/arrow:translate-x-1 transition-transform"
            />
          </Button>
        </div>
      </div>


      <div class="relative group mt-8 w-[100%]">
        <!-- gradient shadow -->
        <div class="absolute -top-6 right-12 w-[100%] md:w-[70%] h-12 lg:h-[80%] bg-primary/50 blur-3xl rounded-full img-shadow-animation" />

        <div class="w-[100%] md:w-[70%] aspect-video mx-auto bg-gradient-to-r from-primary to-[#D247BF] rounded p-1 img-border-animation">
          <video autoplay loop muted playsinline class="w-full md:w-[100%] mx-auto aspect-video relative leading-none flex items-center">
            <source src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/WhatCarCanYouGetForAGrand.mp4" type="video/mp4" />
          </video>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.img-shadow-animation {
  animation-name: img-shadow-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

.img-border-animation {
  animation-name: img-border-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

@keyframes img-shadow-animation {
  from {
    opacity: 0.5;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0px);
  }
}
@keyframes img-border-animation {
  from {
    @apply border-t-primary/10;
  }

  to {
    @apply border-t-primary/60;
  }
}
</style>
