<template>
  <div
    class="py-6 sm:py-8 lg:py-10 xl:py-12 grid gap-y-6 sm:grid-cols-2 sm:gap-8 lg:grid-cols-3 border-t border-gray-200"
  >
    <OrganismFooterLinks
      title="Guides"
      :links="[
        { title: 'Concepts' },
        { title: 'Features' },
        { title: 'Directory Structure' }
      ]"
    />
    <OrganismFooterLinks
      title="Glossaries"
      :links="[
        { title: 'Configuration' },
        { title: 'Components' },
        { title: 'Internals' }
      ]"
    />
    <div class="bg-gray-100 rounded-lg">
      <NuxtLink
        to="/"
        class="-m-3 p-3 flex items-start space-x-4 transition ease-in-out duration-150"
      >
        <!-- Heroicon name: chart-bar -->
        <svg
          class="flex-shrink-0 h-6 w-6 text-indigo-600"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"
          />
        </svg>
        <div class="space-y-1">
          <p class="text-base leading-6 font-medium text-gray-900">
Link
</p>
          <p class="text-sm leading-5 text-gray-500">
            Get a better understanding of where your traffic is coming from.
          </p>
        </div>
      </NuxtLink>
    </div>
  </div>
</template>
