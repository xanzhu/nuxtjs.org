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
        class="py-6 sm:py-8 lg:py-10 xl:pt-12 xl:pb-16 grid gap-y-6 sm:grid-cols-2 sm:gap-8 lg:grid-cols-5 border-t border-gray-200"
      >
        <div class="col-span-3 grid grid-cols-2">
          <MoleculeListLinks
            v-for="(group, title) in links"
            :key="title"
            :title="title"
            :links="group"
          />
        </div>
        <div
          v-if="featured"
          class="bg-gray-100 rounded-lg col-span-2 hover:bg-gray-200"
        >
          <NuxtLink
            to="/"
            class="h-full p-4 flex justify-start items-center transition ease-in-out duration-150"
          >
            <svg-icon
              name="illustrations/discover"
              class="w-24 h-24 mx-2 inline-block"
            />
            <div class="pl-4">
              <p class="text-base leading-6 font-medium text-gray-900 pb-1">
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
