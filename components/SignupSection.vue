<template>
  <div class="pt-16 pb-20">
    <div id="ethmerge">
      <section class="section">
        <div
          class="container px-4 md:px-0 max-w-screen-xl mx-auto flex items-center justify-center"
        >
          <div class="max-w-[700px] flex flex-col justify-start items-start">
            <!-- <h1 :class="[activeTab === 'two' ? 'text-white' : 'text-[#152c5b]']" class="mb-6 text-2xl text-[#152c5b] md:text-[31px] font-bold">
              Welcome to HyperPay Workbench
            </h1> -->
            
            <div class="flex flex-col items-center justify-center">
              <div v-if="activeTab === 'one'">
                <div>
                  <email-and-password />
                </div>
              </div>

              <div v-if="activeTab === 'two'">
                <div>
                  <dapps />
                </div>
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
  props: {
    activeTab: {
      type: String,
      default: 'one',
    },
  },
  created() {
    if (this.activeTab === 'one') {
      this.$router.push('/custody')
    }
  },
  methods: {
    changeActiveTab(params) {
      console.log(params)
      if (params === 'one') {
        this.$router.push('/custody')
      }
      if (params === 'two') {
        this.$router.push('/web3')
      }
    },
  },
}
</script>

<style></style>
