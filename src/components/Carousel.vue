<script setup>
// If you are using PurgeCSS, make sure to whitelist the carousel CSS classes
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import { ref, onMounted } from 'vue';
const props = defineProps(['height',"navigationTrue"])
const {height,navigationTrue} = props
// Carousel configuration
const config = {
    height: height || "auto",
    itemsToShow: 1,
    gap: 5,
    snapAlign: 'center',

    breakpointMode: 'carousel',
    // Any settings not specified will fall back to the carousel's default settings
    breakpoints: {
        // 400px and up
        640: {
            itemsToShow: 2,
            snapAlign: 'center',
        },
        // 500px and up
        768: {
            itemsToShow: 3,
            snapAlign: 'center',
        },
        1024: {
            itemsToShow: 5,
            snapAlign: 'center',
        },
    },
};
const properties = ref([]);
const data = ref(null);

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
        properties.value = data.value
    } else {
        properties.value = [];
    }
});
</script>

<template>
        <div class="carousel__wrapper">
            <Carousel v-bind="config">
                <Slide v-for="image in properties" :key="image.title">
                    <div class="relative w-full h-full rounded-lg overflow-hidden">
                       
                        <img :src="image.image" alt="image" class="carousel-img" loading="lazy" />
                        <div class="absolute top-0 left-0 w-full h-full bg-black/20"></div>
                        <div class="absolute top-4 left-2 text-white text-lg font-semibold">
                            <h4>{{image.title}}</h4>
                            <span>{{ image.number    }}</span>
                        </div>
                    </div>
                </Slide>

                <template #addons>

                    <Navigation v-if="navigationTrue" />
                    <Pagination :paginateByItemsToShow="true" :style="navigationTrue ? '' : 'bottom: -2.5em;'" />
                </template>
            </Carousel>
        </div>
</template>

<style>
.carousel-img {
    border-radius: 8px;
    width: 100%;
    height: 100%;
    object-fit: cover;
}

/* carousel */
.carousel__pagination-button {
    height: 5px;
    width: 5px;
    padding: 5px;
    border-radius: 100%;
    background-color: gainsboro;
}

.carousel__pagination-button--active {
    background-color: black;
}

.carousel__wrapper {
    /* resize: horizontal; */
    /* border: 2px dashed gray; */
    overflow: visible;
    /* max-width: 688px; */
    min-height: 100%;
    padding: 2px;
}

</style>