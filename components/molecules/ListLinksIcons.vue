<template>
  <div class="flex justify-between items-center py-4">
    <a
      v-for="link in links"
      :key="link.icon"
      href="https://github.com/nuxt/nuxt.js"
      class="inline-block p-1 text-gray-500 hover:text-gray-700 dark:hover:text-gray-300"
      target="_blank"
      rel="noopener"
    >
      <svg-icon :name="'feather/' + link.icon" class="h-5 w-5 text-gray-500" />
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          icon: 'twitter',
          href: 'https://twitter.com/nuxt_js'
        },
        {
          icon: 'youtube',
          href: 'https://github.com/nuxt/nuxt.js'
        },
        {
          icon: 'instagram',
          href: 'https://github.com/nuxt/nuxt.js'
        },
        {
          icon: 'linkedin',
          href: 'https://github.com/nuxt/nuxt.js'
        },
        {
          icon: 'codesandbox',
          href: 'https://github.com/nuxt/nuxt.js'
        },
        {
          icon: 'github',
          href: 'https://github.com/nuxt/nuxt.js'
        }
      ]
    }
  }
}
</script>
