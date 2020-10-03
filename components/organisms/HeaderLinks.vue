<template>
  <nav class="hidden lg:flex lg:pt-1 xl:pt-0 mx-auto">
    <ul class="flex text-center">
      <li
        v-for="(links, link) in $t('header.links')"
        :key="link"
        class="xl:px-6 lg:py-0 lg:px-4 py-2"
      >
        <button
          type="button"
          class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-gray-100 inline-flex items-center space-x-2 text-base leading-6 focus:outline-none focus:text-gray-900 transition ease-in-out duration-150 capitalize tracking-wide font-medium"
          :class="{ 'border-b-1 border-gray-900': value === link }"
          @click.prevent="$emit('input', value === link ? '' : link)"
        >
          <span>{{ link }}</span>
          <!--
            Heroicon name: chevron-down

            Item active: "text-gray-600", Item inactive: "text-gray-400"
          -->
          <svg
            class="block lg:hidden text-gray-400 h-5 w-5 group-hover:text-gray-500 group-focus:text-gray-500 transition ease-in-out duration-150"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
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
  }
}
</script>
