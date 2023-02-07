<template>
  <div class="bg-[#0a1829]">
    <div class="max-w-screen-xl mx-auto w-full">
      <nav
        class="w-full h-[60px] md:h-[70px] px-4 max-w-screen-xl mx-auto navbar flex justify-between items-center is-transparent"
        role="navigation"
        aria-label="main navigation"
      >
        <div class="navbar-brand">
          <a class="navbar-item flex items-center" href="/">
            <img class="h-9" src="@/assets/images/logo-hyper.svg" alt="" />
          </a>
        </div>
        <div class="hidden lg:block text-white text-lg font-semibold">
          <nav>
            <ul class="flex space-x-7">
              <li>
                <div class="flex">
                  <nuxt-link to="/">Earn</nuxt-link>
                  <svg
                    class="w-6 MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv"
                    focusable="false"
                    style="fill: #160042"
                    aria-hidden="true"
                    viewBox="0 0 24 24"
                    data-testid="ArrowDropDownIcon"
                  >
                    <path d="m7 10 5 5 5-5z"></path>
                  </svg>
                </div>
              </li>
              <li>
                <div class="flex">
                  <nuxt-link to="/">Card</nuxt-link>
                  <svg
                    class="w-6 MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv"
                    focusable="false"
                    style="fill: #160042"
                    aria-hidden="true"
                    viewBox="0 0 24 24"
                    data-testid="ArrowDropDownIcon"
                  >
                    <path d="m7 10 5 5 5-5z"></path>
                  </svg>
                </div>
              </li>
              <li>
                <div class="flex">
                  <nuxt-link to="/">Transfer</nuxt-link>
                  <svg
                    class="w-6 MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv"
                    focusable="false"
                    style="fill: #160042"
                    aria-hidden="true"
                    viewBox="0 0 24 24"
                    data-testid="ArrowDropDownIcon"
                  >
                    <path d="m7 10 5 5 5-5z"></path>
                  </svg>
                </div>
              </li>
              <li><nuxt-link to="/">Referral</nuxt-link></li>
              <li class="relative text-[#642eff]">
                <div>
                  <span><nuxt-link to="/">Claim Reward</nuxt-link></span>
                  <span
                    class="absolute bg-red-500 ml-1 text-white font-normal text-xs px-1 rounded-full"
                    >new</span
                  >
                </div>
              </li>
            </ul>
          </nav>
        </div>

        <div>
          <v-google-translate :languages="arrayOfCountries" />
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arrayOfCountries: [
        {
          code: 'en',
          name: 'English',
          cname: '英语',
          ename: 'English',
        },
        {
          code: 'zh-CN',
          name: 'Chinese (Simplified)',
          cname: '中文 (简体)',
          ename: 'Chinese (Simplified)',
        },
        {
          code: 'zh-TW',
          name: 'Chinese (Traditional)',
          cname: '中文 (繁体)',
          ename: 'Chinese (Traditional)',
        },
      ],
    }
  },
}
</script>

<style>
.eo__dropdown__activator {
  color: #3377f8;
  font-weight: 600;
}

.eo__dropdown__menu {
  left: -110px !important;
}

.eo__dropdown__activator .icon-svg {
  fill: #3377f8;
}
</style>
