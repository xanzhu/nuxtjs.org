<template>
  <div>
    <h4
      class="text-sm leading-5 font-semibold tracking-wider text-gray-500 uppercase"
    >
      {{ title }}
    </h4>
    <ul class="mt-6">
      <li v-for="(link, i) in links" :key="i" :class="{ 'mt-5': i > 0 }">
        <NuxtLink
          v-if="link.to"
          :to="link.to"
          class="flex justify-start items-center text-base leading-6 text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-gray-100"
        >
          <svg-icon
            v-if="link.icon"
            :name="'feather/' + link.icon"
            class="text-gray-500 w-4 h-4 mr-2 inline-block"
          />
          <span>{{ link.title }}</span>
        </NuxtLink>
        <a
          v-else
          :href="link.href"
          target="_blank"
          class="flex justify-start items-center text-base leading-6 text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-gray-100"
        >
          <svg-icon
            v-if="link.icon"
            :name="'feather/' + link.icon"
            class="text-gray-500 w-4 h-4 mr-2 inline-block"
          />
          <span>{{ link.title }}</span>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    links: {
      type: Array,
      required: true
    }
  }
}
</script>
