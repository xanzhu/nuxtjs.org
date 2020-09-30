<template>
  <header
    class="fixed top-0 left-0 right-0 z-30 bg-light-elevatedSurface dark:bg-dark-elevatedSurface border-b border-light-border dark:border-dark-border lg:border-0 h-16 lg:h-24 transition-colors duration-300 ease-linear"
    :class="{ shadow: !onTop }"
  >
    <div
      class="container relative mx-auto px-4 flex items-center lg:py-6 h-full"
    >
      <!-- Logo -->
      <NuxtLink
        class="inline-block text-nuxt-gray h-7 lg:h-10 z-10 mr-auto"
        to="/"
        @click.native.right.stop.prevent="$router.push('/design')"
      >
        <h1 class="m-0 h-0 w-0 overflow-hidden">
NUXTJS
</h1>
        <NuxtLogo
          class="h-6 lg:h-8 text-nuxt-gray dark:text-white transition-colors duration-300 ease-linear"
        />
      </NuxtLink>
      <!-- Center Navigation -->
      <OrganismHeaderLinks />
      <!-- Algolia Search -->
      <AlgoliaSearch />
    </div>
    <!-- <OrganismHeaderDropdown /> -->
  </header>
</template>

<script>
import NuxtLogo from '~/assets/images/logo.svg?inline'

export default {
  components: {
    NuxtLogo
  },
  data() {
    return {
      onTop: true
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.onTop = window.pageYOffset === 0
    }
  }
}
</script>
