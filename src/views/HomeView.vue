
<template>
  <main class="min-h-screen" >
    <Hero />

    <FirstSection />

    <CarouselSection />

    <HowItworksSection />

    <FouthSection />

    <BestPropertiesSection />

    <MeetOurTeamSection />
    
  </main>
</template>

<script setup>
import Hero from '@/components/sections/Hero.vue'
import FirstSection from '@/components/sections/FirstSection.vue';
import CarouselSection from '@/components/sections/CarouselSection.vue';
import HowItworksSection from '@/components/sections/HowItworksSection.vue';
import FouthSection from '@/components/sections/FouthSection.vue';
import BestPropertiesSection from '@/components/sections/BestPropertiesSection.vue';
import MeetOurTeamSection from '@/components/sections/MeetOurTeamSection.vue';

</script>