<template>
  <div class="pt-20 pb-20">
    <div id="ethmerge">
      <section class="section">
        <div class="container px-4 md:px-0 max-w-screen-xl mx-auto">
          <div class="text-white flex flex-col items-center justify-center">
            <div
              class="max-w-[700px] rounded-lg w-full py-6 px-5 md:py-12 md:px-12 bg-white"
              style="box-shadow: 0 0 20px 1px rgb(166 179 207 / 30%)"
            >
              <h1
                class="mb-12 text-2xl text-[#152c5b] md:text-[31px] font-bold"
              >
                Login to your account
              </h1>
              <div class="my-10 space-x-2 flex">
                <button
                  @click="changeActiveTab('one')"
                  :class="`${
                    activeTab === 'one'
                      ? 'bg-[#185cff] text-white'
                      : 'text-[#185cff]'
                  } border-[#185cff] border rounded-lg p-[15px] font-semibold`"
                >
                  Email or Phone
                </button>
                <button
                  @click="changeActiveTab('two')"
                  :class="`${
                    activeTab === 'two'
                      ? 'bg-[#185cff] text-white'
                      : 'text-[#185cff]'
                  } border-[#185cff] border rounded-lg p-[15px] font-semibold`"
                >
                  Decentralized wallet
                </button>
              </div>

              <div v-if="activeTab === 'one'">
                <email-and-password />
              </div>

              <div v-if="activeTab === 'two'">
               <dapps />
              </div>

            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import Dapps from './Dapps.vue'
import EmailAndPassword from './EmailAndPassword.vue'

export default {
  components: { EmailAndPassword, Dapps },
  data() {
    return {
      activeTab: 'one',
      
    }
  },
  methods: {
    changeActiveTab(params) {
      this.activeTab = params
    },
  },
}
</script>

<style></style>
