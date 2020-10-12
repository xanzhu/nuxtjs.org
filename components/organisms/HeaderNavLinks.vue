<template>
  <div>
    <h2
      class="text-xs leading-5 font-semibold tracking-wide pb-2 text-light-textSecondary uppercase"
    >
      {{ title }}
    </h2>
    <ul
      class="rounded py-1 bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow"
    >
      <li
        v-for="(link, i) in links"
        :key="link.title"
        :class="{ 'border-t border-light-border': i > 0 }"
      >
        <nuxt-link
          :to="link.to"
          class="group flex justify-between items-center p-4 leading-5 font-normal text-sm capitalize text-light-textPrimary hover:text-light-textDefault"
        >
          <span>{{ link.title }}</span>
          <!-- Forward Icon -->
          <svg-icon
            :name="'feather/' + link.icon"
            class="h-4 w-4 text-light-textPrimary group-hover:text-light-primary"
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
