<template>
  <header
    class="fixed top-0 left-0 right-0 z-30"
    :class="{
      shadow: !onTop,
      'bg-light-surface dark:bg-dark-surface': showPrimary,
      'bg-light-elevatedSurface dark:bg-dark-elevatedSurface': !showPrimary
    }"
  >
    <!-- Primary Navigation-->
    <AtomContainer
      class="text-light-default dark:bg-dark-default flex flex-wrap justify-between items-center py-4"
    >
      <!-- Mobile: Menu Button / Close Button / Previous Button-->
      <button
        v-if="showPrimary && primaryLink"
        class="inline-block py-1 pr-1 lg:hidden"
        @click="primaryLink = ''"
      >
        <!-- Previous Icon -->
        <svg-icon name="feather/arrow-left-circle" class="h-5 w-5" />
      </button>
      <button
        v-else
        class="inline-block py-1 pr-1 lg:hidden"
        @click="toggleMenu"
      >
        <!-- Close Icon -->
        <svg-icon v-if="showPrimary" name="feather/x" class="h-5 w-5" />
        <!-- Menu Icon -->
        <svg-icon v-else name="feather/menu" class="h-5 w-5" />
      </button>
      <!-- Logo: Home Link / PrimaryLink Title-->
      <h1
        v-if="primaryLink"
        class="capitalize text-light-textDefault dark:bg-dark-textDefault text-base lg:hidden"
      >
        {{ primaryLink }}
      </h1>
      <NuxtLink
        v-else
        class="inline-block -mt-1 p-1"
        to="/"
        @click.native.right.stop.prevent="$router.push('/design')"
      >
        <!-- Hidden title for SEO -->
        <h1 class="m-0 h-0 w-0 overflow-hidden">
NUXTJS
</h1>
        <!-- SVG -->
        <img
          src="@/assets/logos/nuxtjs.svg"
          alt="NuxtJS Logo"
          class="h-5 w-auto inline-block"
        />
      </NuxtLink>
      <!-- Mobile: Search Button / Theme Button-->
      <button v-if="!primaryLink" class="inline-block py-1 pr-1 lg:hidden">
        <!-- Theme Icon -->
        <svg-icon v-if="showPrimary" name="feather/sun" class="h-5 w-5" />
        <!-- Search Icon -->
        <svg-icon v-else name="feather/search" class="h-5 w-5" />
      </button>
      <div v-else class="h-5 w-5 lg:hidden"></div>
      <!-- Center Navigation -->
      <OrganismHeaderNav
        v-model="primaryLink"
        :class="{ hidden: !showPrimary }"
      />
      <!-- Algolia Search -->
      <!-- Todo: Replace with New algolia Search (Ask Benjamin) <AlgoliaSearch /> -->
    </AtomContainer>
    <!-- Secondary Navigation -->
    <OrganismHeaderDropdown :current="primaryLink" />
  </header>
</template>

<script>
export default {
  data() {
    return {
      onTop: true,
      showPrimary: false,
      primaryLink: ''
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
    },
    toggleMenu() {
      this.showPrimary = !this.showPrimary
      this.primaryLink = ''
    }
  }
}
</script>
