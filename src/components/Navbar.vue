<script lang="ts" setup>
import { ref } from "vue";

import { useColorMode } from "@vueuse/core";
const mode = useColorMode();
mode.value = "dark";

import {
  NavigationMenu,
  NavigationMenuItem,
  NavigationMenuLink,
  NavigationMenuList,
} from "@/components/ui/navigation-menu";
import {
  Sheet,
  SheetContent,
  SheetFooter,
  SheetTrigger,
} from "@/components/ui/sheet";

import { Button } from "@/components/ui/button";
import { Separator } from "@/components/ui/separator";

import { Menu } from "lucide-vue-next";
import ToggleTheme from "./ToggleTheme.vue";

import TiktokIcon from "@/icons/TiktokIcon.vue";
import InstagramIcon from "@/icons/InstagramIcon.vue";
import YoutubeIcon from "@/icons/YoutubeIcon.vue";
import TwitchIcon from "@/icons/TwitchIcon.vue";

interface RouteProps {
  component: any;
  href: string;
  label: string;
}

const routeList: RouteProps[] = [
  {
    component: TiktokIcon,
    href: "https://www.tiktok.com/@luqeno",
    label: "TikTok",
  },
  {
    component: InstagramIcon,
    href: "https://www.instagram.com/luqeno",
    label: "Instagram",
  },
  {
    component: YoutubeIcon,
    href: "https://www.youtube.com/@luqeno",
    label: "YouTube",
  },
  {
    component: TwitchIcon,
    href: "https://www.twitch.tv/luqeno",
    label: "Twitch",
  },
];

const isOpen = ref<boolean>(false);
</script>

<template>
  <header class="w-[90%] md:w-[70%] lg:w-[75%] lg:max-w-screen-xl top-5 mx-auto sticky z-40 flex justify-between items-center p-2">
    <!-- Mobile -->
    <div class="flex items-center lg:hidden">
      <Sheet v-model:open="isOpen">
        <SheetTrigger as-child>
          <Menu
            @click="isOpen = true"
            class="cursor-pointer"
          />
        </SheetTrigger>

        <SheetContent
          side="left"
          class="flex flex-col justify-between rounded-tr-2xl rounded-br-2xl bg-card"
        >
          <div>
            <div class="flex flex-col gap-2">
              <Button
                v-for="{ href, label } in routeList"
                :key="label"
                as-child
                variant="ghost"
                class="justify-start text-base"
              >
                <a
                  @click="isOpen = false"
                  :href="href"
                >
                  {{ label }}
                </a>
              </Button>
            </div>
          </div>

          <SheetFooter class="flex-col sm:flex-col justify-start items-start">
            <Separator class="mb-2" />

            <ToggleTheme />
          </SheetFooter>
        </SheetContent>
      </Sheet>
    </div>

    <!-- Desktop -->
    <div class="hidden lg:flex">
      <ToggleTheme />
    </div>

    <NavigationMenu class="hidden lg:block">
      <NavigationMenuList>
        <NavigationMenuItem>
          <NavigationMenuLink asChild>
            <Button
              v-for="{ component, href, label } in routeList"
              :key="label"
              as-child
              variant="ghost"
              class="justify-start text-base"
            >
              <a :href="href" target="_blank">
                <component :is="component" />
              </a>
            </Button>
          </NavigationMenuLink>
        </NavigationMenuItem>
      </NavigationMenuList>
    </NavigationMenu>
  </header>
</template>

<style scoped>
.shadow-light {
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.085);
}

.shadow-dark {
  box-shadow: inset 0 0 5px rgba(255, 255, 255, 0.141);
}
</style>
