<template>
  <div>
    <HeroSection />
    <MergeSection />
    <AboutSection />
  </div>
</template>

<script>
import MergeSection from '~/components/MergeSection.vue';
import AboutSection from '~/components/AboutSection.vue';
import HeroSection from '~/components/HeroSection.vue';
export default {
    name: "IndexPage",
    components: { MergeSection, AboutSection, HeroSection }
}
</script>
