<template>
    <!-- <a
      href="#"
      class="flex items-center justify-between gap-1 bg-white/15 backdrop-blur-sm rounded-full px-1 w-32 sm:w-36 py-1"
    >
      <div class="p-2 bg-white rounded-full">
        <component :is="getIconComponent(icon)" />
      </div>
      <p class="text-center flex-1 capitalize text-sm sm:text-base">
        {{ title }}
      </p>
    </a> -->
    <div class="p-4">
        <component class="mx-auto" :is="getIconComponent(icon)" />
        <h2 class="text-md font-semibold capitalize text-center">{{ title }}</h2>
        <p class="text-base text-center">{{ subTitle }}</p>
    </div>
  </template>
  <script setup>
  const props = defineProps(["title","subTitle" ,"icon"]);
  
  import widerangeofproperties from "@/components/icons/widerangeofproperties.vue";
  import buyorrenthomes from "@/components/icons/buyorrenthomes.vue";
  import trustedbythousands from "@/components/icons/trustedbythousands.vue";
  
  const getIconComponent = (icon) => {
    switch (icon) {
      case "widerangeofproperties":
        return widerangeofproperties;
      case "buyorrenthomes":
        return buyorrenthomes;
      case "trustedbythousands":
        return trustedbythousands;
      default:
        return widerangeofproperties;
    }
  };
  </script>
  