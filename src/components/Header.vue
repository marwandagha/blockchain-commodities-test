<template>
  <header>
    <div class="text-center mt-3 mb-3">
      <img class="logo-width" src="../assets/img/blockchain-commodities-logo-white.svg" />
    </div>
  </header>
</template>

<script>

export default {
  name: 'Header',

  computed: {
    // homePage() {
    //   if (this.$route.path === '/') {
    //     return true
    //   } else {
    //     return false
    //   }
    // },
  },
}
</script>

<style scoped>

.logo-width {
  width: 30%
}
</style>


