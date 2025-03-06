<template>
  <main >
    <MainSectionTitle
      title="why you should work with us"
      sub-title="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
    />

    <div class="my-8 grid grid-cols-1 md:grid-cols-3   gap-4 container mx-auto">
      <FirstSectionCard
        title="wide range of properties"
        sub-title="We offer expert legal help for all related property
                    items in Dubai."
        icon="widerangeofproperties"
      />
      <FirstSectionCard
        title="buy or rent homes"
        sub-title="We sell your home at the best market price and very
quickly as well."
        icon="buyorrenthomes"
      />
      <FirstSectionCard
        title="trusted by thousands"
        sub-title="We offer you free consultancy to get a loan for your
new home."
        icon="trustedbythousands"
      />
    </div>

    <MainSectionTitle
      title="Featured Properties"
      sub-title="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
    />

  </main>
</template>

<script setup>
import MainSectionTitle from "@/components/MainSectionTitle.vue";
import FirstSectionCard from "@/components/cards/FristSectionCard.vue";
</script>
