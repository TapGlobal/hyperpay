<template>
  <div class="flex-1 bg-[#0a1829]">
    <SignupSection activeTab="one" />
  </div>
</template>

<script>
import SignupSection from '~/components/SignupSection.vue';
export default {
    name: "IndexPage",
    components: { SignupSection }
}
</script>
