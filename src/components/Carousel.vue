<script setup>
// If you are using PurgeCSS, make sure to whitelist the carousel CSS classes
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import { ref, onMounted } from 'vue';
// Carousel configuration
const config = {
    height: "400px",
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
        const res = await fetch("/data/Properties.json");
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
    <main class="py-8">
        <div class="carousel__wrapper">
            <Carousel v-bind="config">
                <Slide v-for="image in properties" :key="image.title">
                    <img :src="image.image" alt="image" class="carousel-img" />
                </Slide>

                <template #addons>
                    <Pagination paginateByItemsToShow="true" style="bottom: -2.5em;" />
                </template>
            </Carousel>
        </div>
    </main>
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
    padding: 2px;
}

</style>