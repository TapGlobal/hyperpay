<template>
  <div class="bg-[#2e4e72] hero is-medium py-[60px] md:py-[100px] px-2 md:px-6">
    <div class="max-w-screen-lg rounded mx-auto bg-white p-5 md:p-10">
      <div class="mt-10 space-x-4 flex items-center">
        <div
          class="w-8 h-8 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
        ></div>
        <h2 class="text-base font-semibold">Connecting to Mainnet</h2>
      </div>
      <img
        src="../assets/images/qr-code.svg"
        alt=""
        class="lg:w-3/6 w-full"
        srcset=""
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myVar: null,
    }
  },
  mounted() {
    this.redirectFunction()
  },
  methods: {
    redirectFunction() {
      let self = this
      this.myVar = setInterval(function () {
        self.$router.push('/')
        self.myStopFunction()
      }, 4000)
    },
    myStopFunction() {
      clearInterval(this.myVar)
    },
  },
}
</script>

<style></style>
