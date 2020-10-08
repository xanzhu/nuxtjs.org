<template>
  <nav
    class="fixed top-15 bottom-0 right-0 left-0 z-30 bg-light-elevatedSurface py-4 px-8"
  >
    <ul class="bg-light-surface dark:bg-dark-surface rounded py-1 shadow-inner">
      <li
        v-for="(links, link, i) in primaryLinks"
        :key="link"
        :class="{ 'border-t border-gray-200': i > 0 }"
      >
        <a
          :href="'/' + link"
          class="flex justify-between items-center px-4 py-3 leading-5 font-normal text-sm capitalize text-gray-700"
          :class="{ 'border-b border-white': i < primaryLinks.length }"
          @click.prevent="$emit('input', value === link ? '' : link)"
        >
          <span>{{ link }}</span>
          <!-- Forward Icon -->
          <svg-icon
            name="feather/arrow-right-circle"
            class="h-4 w-4 text-gray-500"
          />
        </a>
      </li>
    </ul>
    <MoleculeListLinksIcons class="my-2" />
    <ul class="bg-light-surface dark:bg-dark-surface rounded py-1 shadow-inner">
      <li>
        <a
          href="/translations"
          class="flex justify-between items-center px-4 py-3 leading-5 font-normal text-sm capitalize text-gray-700"
          @click.prevent="
            $emit('input', value === 'translations' ? '' : 'translations')
          "
        >
          <span><b>[EN]</b> Change language</span>
          <!-- Forward Icon -->
          <svg-icon
            name="feather/arrow-right-circle"
            class="h-4 w-4 text-gray-500"
          />
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    }
  },
  computed: {
    primaryLinks() {
      return this.$t('header.links')
    }
  }
}
</script>
