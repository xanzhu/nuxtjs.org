<template>
  <div>
    <h2
      class="text-xs leading-5 font-semibold tracking-wide pb-2 text-gray-500 uppercase"
    >
      {{ title }}
    </h2>
    <ul
      class="rounded py-1 bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow"
    >
      <li
        v-for="(link, i) in links"
        :key="link.title"
        :class="{ 'border-t border-gray-200': i > 0 }"
      >
        <nuxt-link
          :to="link.to"
          class="flex justify-between items-center px-4 py-3 leading-5 font-normal text-sm capitalize text-gray-700"
          :class="{ 'border-b border-white': i < links.length }"
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
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: 'Title'
    },
    links: {
      type: Array,
      required: true
    }
  }
}
</script>
