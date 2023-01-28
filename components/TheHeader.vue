<template>
  <div class="bg-white max-w-screen-xl mx-auto w-full">
    <nav
      class="w-full h-[60px] md:h-[70px] px-4 max-w-screen-xl mx-auto navbar flex justify-between items-center is-transparent"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand">
        <a class="navbar-item flex items-center" href="/">
          <img class="" src="../assets/images/tap-logo.svg" alt="" />
        </a>
      </div>
      <div class="hidden lg:block text-[#160042] text-lg font-semibold">
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
      <button
        class="flex text-xl font-semibold items-center text-[#3377f8]"
        tabindex="0"
        type="button"
      >
        <svg
          class="w-6 mr-2 MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-hjmalu"
          focusable="false"
          style="fill: #3377f8"
          aria-hidden="true"
          viewBox="0 0 24 24"
          data-testid="TranslateIcon"
        >
          <path
            d="m12.87 15.07-2.54-2.51.03-.03c1.74-1.94 2.98-4.17 3.71-6.53H17V4h-7V2H8v2H1v1.99h11.17C11.5 7.92 10.44 9.75 9 11.35 8.07 10.32 7.3 9.19 6.69 8h-2c.73 1.63 1.73 3.17 2.98 4.56l-5.09 5.02L4 19l5-5 3.11 3.11.76-2.04zM18.5 10h-2L12 22h2l1.12-3h4.75L21 22h2l-4.5-12zm-2.62 7 1.62-4.33L19.12 17h-3.24z"
          ></path>
        </svg>
        <p class="MuiTypography-root MuiTypography-body1 css-2pbqks">English</p>
        <svg
          class="w-6 MuiSvgIcon-root MuiSvgIcon-fontSizeMedium css-vubbuv"
          focusable="false"
          style="fill: #3377f8"
          aria-hidden="true"
          viewBox="0 0 24 24"
          data-testid="ArrowDropDownIcon"
        >
          <path d="m7 10 5 5 5-5z"></path></svg
        ><span class="MuiTouchRipple-root css-w0pj6f"></span>
      </button>
    </nav>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
