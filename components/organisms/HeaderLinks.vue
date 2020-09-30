<template>
  <nav class="hidden lg:flex lg:pt-1 xl:pt-0 mx-auto">
    <ul class="flex text-center font-medium tracking-wide">
      <li
        v-for="link in $t('header.links')"
        :key="link.slug"
        class="xl:px-4 lg:py-0 lg:px-2 py-2"
      >
        <NuxtLink
          v-if="link.type === 'newDocs'"
          class="block hover:no-underline hover:text-nuxt-lightgreen text-nuxt-gray dark:text-dark-onSurfacePrimary"
          :to="
            localePath({
              name: link.routeName,
              params: {
                section: 'guides',
                book: 'get-started',
                slug: 'installation'
              }
            })
          "
        >
          {{ link.name }}
          <span
            class="bg-green-200 dark:text-black text-ss align-top px-1 rounded-sm lowercase"
          >
            beta
          </span>
        </NuxtLink>
        <NuxtLink
          v-if="link.type === 'dynamic'"
          class="block hover:no-underline hover:text-nuxt-lightgreen text-nuxt-gray dark:text-dark-onSurfacePrimary"
          :to="
            localePath({
              name: link.routeName,
              params: { section: link.slug }
            })
          "
        >
          {{ link.name }}
        </NuxtLink>
        <NuxtLink
          v-else-if="link.type === 'static'"
          class="block hover:no-underline hover:text-nuxt-lightgreen text-nuxt-gray dark:text-dark-onSurfacePrimary"
          :to="localePath({ name: link.slug })"
        >
          {{ link.name }}
        </NuxtLink>
        <a
          v-else-if="link.type === 'external'"
          :key="link.href"
          :href="link.href"
          class="block hover:no-underline hover:text-nuxt-lightgreen text-nuxt-gray dark:text-dark-onSurfacePrimary"
        >
          {{ link.name }}
        </a>
      </li>
    </ul>
  </nav>
</template>
