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
    class="absolute inset-x-0 transform shadow-dropdown bg-white"
    :class="{ hidden: !current }"
  >
    <div class="mx-auto container px-4 sm:px-6 lg:px-8">
      <MoleculeDropdownLearn />
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
      return this.current.length ? this.$t('header.links')[this.current] : null
    }
  }
}
</script>
