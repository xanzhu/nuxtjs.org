<template>
  <nav
    class="fixed top-15 bottom-0 right-0 left-0 z-30 pt-4 p-8 overflow-y-auto"
    :class="
      value
        ? 'bg-light-surface dark:bg-dark-surface'
        : 'bg-light-elevatedSurface dark:bg-dark-elevatedSurface'
    "
  >
    <div v-if="value">
      <!-- Secondary Links -->
      <!-- <div>
        Featured
      </div> -->
      <div v-for="(group, title, n) in navLinks" :key="title">
        <h2
          class="text-xs leading-5 font-semibold tracking-wide pb-2 text-gray-500 uppercase"
          :class="{ 'pt-8': n > 0 }"
        >
          {{ title }}
        </h2>
        <ul
          class="rounded py-1 bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow"
        >
          <li
            v-for="(link, i) in group"
            :key="link.title"
            :class="{ 'border-t border-gray-200': i > 0 }"
          >
            <nuxt-link
              :to="link.to"
              class="flex justify-between items-center px-4 py-3 leading-5 font-normal text-sm capitalize text-gray-700"
              :class="{ 'border-b border-white': i < group.length }"
            >
              <span>{{ link.title }}</span>
              <!-- Forward Icon -->
              <svg-icon
                :name="'feather/' + link.icon"
                class="h-4 w-4 text-gray-500"
              />
            </nuxt-link>
          </li>
        </ul>
      </div>
    </div>
    <div v-else>
      <!-- PrimaryLinks -->
      <ul
        class="rounded py-1 bg-light-surface dark:bg-dark-surface shadow-inner"
      >
        <li
          v-for="(links, group, i) in navLinks"
          :key="group"
          :class="{ 'border-t border-gray-200': i > 0 }"
        >
          <a
            :href="'/' + group"
            class="flex justify-between items-center px-4 py-3 leading-5 font-normal text-sm capitalize text-gray-700"
            :class="{ 'border-b border-white': i < navLinks.length }"
            @click.prevent="$emit('input', value === group ? '' : group)"
          >
            <span>{{ group }}</span>
            <!-- Forward Icon -->
            <svg-icon
              name="feather/arrow-right-circle"
              class="h-4 w-4 text-gray-500"
            />
          </a>
        </li>
      </ul>
      <!-- Translation Link -->
      <ul
        class="rounded bg-light-surface dark:bg-dark-surface shadow-inner mt-8"
      >
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
    </div>
    <MoleculeListLinksIcons class="mt-4" />
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
    navLinks() {
      let links = this.$t('header.links')
      if (this.value) {
        links = Object.assign({}, this.$t('header.links')[this.value])
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
