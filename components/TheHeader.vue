<template>
  <div class="bg-[#2e4e72] px-6">
    <nav
      class="w-full h-[60px] md:h-[80px] max-w-screen-xl mx-auto navbar flex justify-between items-center is-transparent"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand md:w-2/12">
        <a class="navbar-item" href="/"
          ><img
            class="w-[100px] md:w-[240px]"
            src="https://ava.do/static/media/avado-logo-v1.1.60dfafad.svg"
            alt="AVADO: Your personal gateway to the decentralized web"
            /></a
        >
      </div>
      <div id="navMenu" class="md:w-9/12 flex navbar-menu">
        <div class="navbar-end w-full justify-between flex items-center">
          <div class="space-x-6 hidden md:block">
            <a class="navbar-item text-[#f8f8ff] text" href="/#about">About</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/#ryo-cloud"
              >AVADO cloud</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/#dappstore"
              >DappStore</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/#use-cases"
              >Use cases</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/#hardware"
              >Hardware</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/merge-node"
              >Your DApp on AVADO</a
            ><a class="navbar-item text-[#f8f8ff] text" href="/merge-node">Blog</a>
          </div>
          <div class="ml-3 navbar-item">
            <div class="field is-grouped">
              <p class="control">
                <a
                  class="button buttonmargin is-success is-outlined is-medium"
                  href="/merge-node"
                  >Order my AVADO</a
                >
              </p>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
