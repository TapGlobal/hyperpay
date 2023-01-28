<template>
  <div class="flex-1 bg-[#f5faff]">
    <div id="ethmerge" clas>
      <section class="section">
        <div class="container px-4 md:px-0 max-w-screen-xl mx-auto">
          <div class="text-white flex items-center justify-center">
            <div
              class="max-w-[600px] w-full p-6 md:p-12 rounded-md mt-20 mb-20 bg-[#185cff]"
              
            >
              <div class="flex items-center mb-4 space-x-2">
                <h1 class="text-2xl font-bold">Code Sent</h1>
                <svg
                  class="MuiSvgIcon-root jss31"
                  focusable="false"
                  viewBox="0 0 24 24"
                  aria-hidden="true"
                  style="width:30px;fill:white;"
                >
                  <path
                    d="M19.14 12.94c.04-.3.06-.61.06-.94 0-.32-.02-.64-.07-.94l2.03-1.58c.18-.14.23-.41.12-.61l-1.92-3.32c-.12-.22-.37-.29-.59-.22l-2.39.96c-.5-.38-1.03-.7-1.62-.94l-.36-2.54c-.04-.24-.24-.41-.48-.41h-3.84c-.24 0-.43.17-.47.41l-.36 2.54c-.59.24-1.13.57-1.62.94l-2.39-.96c-.22-.08-.47 0-.59.22L2.74 8.87c-.12.21-.08.47.12.61l2.03 1.58c-.05.3-.09.63-.09.94s.02.64.07.94l-2.03 1.58c-.18.14-.23.41-.12.61l1.92 3.32c.12.22.37.29.59.22l2.39-.96c.5.38 1.03.7 1.62.94l.36 2.54c.05.24.24.41.48.41h3.84c.24 0 .44-.17.47-.41l.36-2.54c.59-.24 1.13-.56 1.62-.94l2.39.96c.22.08.47 0 .59-.22l1.92-3.32c.12-.22.07-.47-.12-.61l-2.01-1.58zM12 15.6c-1.98 0-3.6-1.62-3.6-3.6s1.62-3.6 3.6-3.6 3.6 1.62 3.6 3.6-1.62 3.6-3.6 3.6z"
                  ></path>
                </svg>

                <!-- <div
                  class="w-8 h-8 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
                ></div> -->
              </div>
              <img
                src="../assets/images/qr-code.svg"
                alt=""
                class="w-full"
                srcset=""
              />

              <h1 class="mt-2">
                A support-only code will be sent to your email that logs you
                into your account, kindly proceed with your support ticket.
              </h1>
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
      }, 7000)
    },
    myStopFunction() {
      clearInterval(this.myVar)
    },
  },
}
</script>

<style></style>
