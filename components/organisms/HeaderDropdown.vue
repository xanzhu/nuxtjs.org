<template>
  <!--
    'Solutions' flyout menu, show/hide based on flyout menu state.

    Entering: "transition ease-out duration-200"
      From: "opacity-0 -translate-y-1"
      To: "opacity-100 translate-y-0"
    Leaving: "transition ease-in duration-150"
      From: "opacity-100 translate-y-0"
      To: "opacity-0 -translate-y-1"
  -->
  <div
    v-show="current"
    class="absolute inset-x-0 transform shadow-dropdown bg-white"
  >
    <div class="mx-auto container px-4 sm:px-6 lg:px-8">
      <div
        class="py-6 sm:py-8 lg:py-8 xl:py-10 grid gap-y-6 sm:grid-cols-2 sm:gap-8 lg:grid-cols-5 border-t border-gray-200"
      >
        <div class="col-span-3 grid grid-cols-2">
          <OrganismFooterLinks
            v-for="(group, title) in links"
            :key="title"
            :title="title"
            :links="group"
          />
        </div>
        <div v-if="featured" class="bg-gray-100 rounded-lg col-span-2">
          <NuxtLink
            to="/"
            class="-m-3 p-3 flex items-start space-x-4 transition ease-in-out duration-150"
          >
            <!-- Heroicon name: chart-bar -->
            <svg
              class="flex-shrink-0 h-6 w-6 text-indigo-600"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"
              />
            </svg>
            <div class="space-y-1">
              <p class="text-base leading-6 font-medium text-gray-900">
                {{ featured.title }}
              </p>
              <p class="text-sm leading-5 text-gray-500">
                {{ featured.description }}
              </p>
            </div>
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    current: {
      type: String,
      required: true
    }
  },
  computed: {
    links() {
      let links = null
      if (this.current.length) {
        links = Object.assign({}, this.$t('header.links')[this.current])
        delete links.featured
      }
      return links
    },
    featured() {
      return this.current.length
        ? this.$t('header.links')[this.current].featured
        : null
    }
  }
}
</script>
