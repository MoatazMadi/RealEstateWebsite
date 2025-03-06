<template>
  <!-- <main class="h-[85vh] relative bg-cover bg-center" style="background-image: url('/imgs/hero.jpg');"> -->

  <main
    class="h-screen relative bg-center bg-cover bg-no-repeat text-[#1F4B43]"
    style="
      font-family: 'Roboto' Roboto;
      /* background-image: url('/imgs/hero.jpg') easy-load  */
    "
  >
    <img
      loading="lazy"
      src="/imgs/hero.jpg"
      alt="hero image"
      class="w-full -z-10 h-full object-cover absolute top-0"
    />

    <div
      class="mx-auto flex flex-col pt-48 justify-center items-center max-w-[800px] px-3"
    >
      <a
        href="#"
        class="rounded-full border uppercase py-1 px-3 sm:px-6 text-xs sm:text-sm hover:bg-white/95 transition-all"
      >
        let us guide your home
      </a>

      <h1
        class="text-2xl sm:text-4xl md:text-6xl my-5 cursor-default font-bold select-none"
      >
        Believe in finding it
      </h1>
      <p class="text-xs sm:text-sm cursor-default select-none">
        Search properties for sale and to rent in the UK
      </p>

      <div
        class="mt-8 bg-white p-1 pl-5 rounded-full w-full items-center flex justify-between"
      >
        <input
          type="text"
          class="flex-1 border-none ring-0 outline-0 h-full text-sm sm:text-base"
          placeholder="Enter Name, Keywords..."
          maxlength="255"
        />
        <button
          class="bg-[#E7C873] rounded-full p-2 sm:p-3 md:p-4 cursor-pointer hover:bg-[#f5dd9c] transition-all"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="size-3 sm:size-5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="m21 21-5.197-5.197m0 0A7.5 7.5 0 1 0 5.196 5.196a7.5 7.5 0 0 0 10.607 10.607Z"
            />
          </svg>
        </button>
      </div>

      <p
        class="mt-12 text-white bg-white/5 backdrop-blur-sm rounded-full px-3 text-base"
      >
        What are you looking for?
      </p>
      <div
        class="mt-4 text-white flex flex-wrap justify-evenly gap-1 sm:gap-3 md:gap-6 items-center"
      >
        <CardHero title="modern villa" icon="modernvilla" />
        <CardHero title="apartment" icon="apartment" />
        <CardHero title="town house" icon="townhouse" />
      </div>
    </div>
  </main>
</template>

<script setup>
import CardHero from "@/components/cards/HeroCard.vue";
</script>
