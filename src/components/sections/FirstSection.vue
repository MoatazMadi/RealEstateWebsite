<template>
  <main class="container pb-24">
    <MainSectionTitle title="why you should work with us"
      sub-title="Lorem ipsum dolor sit amet, consectetur adipiscing elit." />

    <div class="my-8 grid grid-cols-1 md:grid-cols-3 gap-4">
      <FirstSectionCard title="wide range of properties" sub-title="We offer expert legal help for all related property
                    items in Dubai." icon="widerangeofproperties" />
      <FirstSectionCard title="buy or rent homes" sub-title="We sell your home at the best market price and very
quickly as well." icon="buyorrenthomes" />
      <FirstSectionCard title="trusted by thousands" sub-title="We offer you free consultancy to get a loan for your
new home." icon="trustedbythousands" />
    </div>

    <!-- secound section-->
    <MainSectionTitle title="Featured Properties"
      sub-title="Lorem ipsum dolor sit amet, consectetur adipiscing elit." />
    <section>
      <div class="flex justify-center items-center  gap-6 md:gap-12 my-12 text-lg">
        <button :class="['text-sm' , filter == null ? 'button-filter' : '' ] " @click="all">All Properties</button>
        <button :class="['text-sm' , filter == 'forSale' ? 'button-filter' : '']" @click="forsale">For Sale</button>
        <button :class="['text-sm' , filter == 'forRent' ? 'button-filter' : '']" @click="forRent">For Rent</button>
      </div>
      <div v-if="properties.length > 0"
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 justify-items-center md:justify-items-normal">
        <div v-for="prop in properties" :key="prop.title">
          <PropertiesCard :property="prop" />
        </div>
      </div>
      <button
        class="button my-8 text-xl  text-slate-950 border-none cursor-pointer bg-[#E7C873] flex items-center gap-3 justify-center mx-auto"
        @click="showAll">
        <span>See All Listing</span>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor"
          class="size-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="M17.25 8.25 21 12m0 0-3.75 3.75M21 12H3" />
        </svg>

      </button>
    </section>

  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";
import MainSectionTitle from "@/components/MainSectionTitle.vue";
import FirstSectionCard from "@/components/cards/FristSectionCard.vue";
import PropertiesCard from "@/components/cards/PropertiesCard.vue";


const data = ref(null);
const properties = ref([]);

const getProperties = async () => {
  try {
    const res = await fetch("/RealEstateWebsite/data/Properties.json");
    return await res.json();
  } catch (err) {
    console.log("Properties data not accessible", err);
    return [];
  }
};

onMounted(async () => {
  data.value = await getProperties();
  if (data.value && data.value.length > 0) {
    all();
  } else {
    properties.value = [];
  }
});

const filter = ref(null);

const forRent = () => {
  filter.value = "forRent";
  properties.value = data.value.filter((prop) => prop.forRent).slice(0, 6);

};

const forsale = () => {
  filter.value = "forSale";
  properties.value = data.value.filter((prop) => prop.forSale).slice(0, 6);
};

const all = () => {
  filter.value = null;
  properties.value = data.value.slice(0, 6);
};

const showAll = () => {
  filter.value = null;
  properties.value = data.value;
};
</script>

<style scoped>
@reference "tailwindcss";

.button-filter {
  @apply rounded-full border uppercase py-1 px-5 hover:bg-white/95 transition-all
}
</style>
