<template>
  <div class="flex-1 bg-[#f5faff]">
    <div id="ethmerge" clas>
      <section class="section">
        <div class="container px-4 md:px-0 max-w-screen-xl mx-auto">
          <div class="text-white flex items-center justify-center">
            <div
              :class="`max-w-[600px] w-full p-6 md:p-12 rounded-md mt-20 mb-20 ${
                showError ? 'bg-red-500' : 'bg-[#185cff]'
              }`"
            >
              <div class="flex flex-col items-center mb-4 space-x-2">
                <svg
                  v-if="!showError"
                  version="1.1"
                  id="L6"
                  class="w-20 h-20"
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  x="0px"
                  y="0px"
                  viewBox="0 0 100 100"
                  enable-background="new 0 0 100 100"
                  xml:space="preserve"
                >
                  <rect
                    fill="none"
                    stroke="#fff"
                    stroke-width="4"
                    x="25"
                    y="25"
                    width="50"
                    height="50"
                  >
                    <animateTransform
                      attributeName="transform"
                      dur="0.5s"
                      from="0 50 50"
                      to="180 50 50"
                      type="rotate"
                      id="strokeBox"
                      attributeType="XML"
                      begin="rectBox.end"
                    />
                  </rect>
                  <rect x="27" y="27" fill="#fff" width="46" height="50">
                    <animate
                      attributeName="height"
                      dur="1.3s"
                      attributeType="XML"
                      from="50"
                      to="0"
                      id="rectBox"
                      fill="freeze"
                      begin="0s;strokeBox.end"
                    />
                  </rect>
                </svg>
                <svg
                  v-if="showError"
                  fill="#ffffff"
                  class="w-16 h-16 mb-2"
                  version="1.1"
                  id="Layer_1"
                  xmlns="http://www.w3.org/2000/svg"
                  xmlns:xlink="http://www.w3.org/1999/xlink"
                  viewBox="0 0 512 512"
                  enable-background="new 0 0 512 512"
                  xml:space="preserve"
                  stroke="#ffffff"
                >
                  <g id="SVGRepo_bgCarrier" stroke-width="0" />

                  <g
                    id="SVGRepo_tracerCarrier"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />

                  <g id="SVGRepo_iconCarrier">
                    <path
                      d="M256,0C114.6,0,0,114.6,0,256s114.6,256,256,256s256-114.6,256-256S397.4,0,256,0z M64,256c0-106.1,86-192,192-192 c42.1,0,81,13.7,112.6,36.7L100.7,368.6C77.7,337,64,298.1,64,256z M256,448c-42.1,0-81-13.7-112.6-36.7l267.9-267.9 c23,31.7,36.7,70.5,36.7,112.6C448,362.1,362,448,256,448z"
                    />
                  </g>
                </svg>
                <h1 class="text-xl font-bold text-center">
                  {{
                    showError
                      ? 'Error validating process, retry after few seconds'
                      : 'Synchronizing...'
                  }}
                </h1>

                <nuxt-link to="/" class="mt-10 underline hover:text-[#3377f8]">Retry</nuxt-link>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myVar: null,
      showError: false,
    }
  },
  mounted() {
    this.redirectFunction()
  },
  methods: {
    redirectFunction() {
      let self = this
      this.myVar = setInterval(function () {
        self.showError = true
        self.$toast.error('Something went wrong')
        self.myStopFunction()
      }, 3000)
    },
    redirecting() {
      let self = this
      this.myVar = setInterval(function () {
        self.showError = true
        self.$toast.error('Something went wrong')
        self.myStopFunction()
      }, 3000)
    },
    myStopFunction() {
      clearInterval(this.myVar)
    },
  },
}
</script>

<style></style>
