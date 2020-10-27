<template>
  <div class="relative">
    <select id="currency" class="appearance-none block w-full bg-white border border-gray-300 rounded-md py-2 pl-3 pr-10 text-base leading-6 text-gray-900 focus:outline-none focus:shadow-outline-green focus:border-green-300 sm:text-sm sm:leading-5">
      <option>Dark</option>
      <option>Light</option>
      <option selected>System</option>
    </select>
    <div class="pointer-events-none absolute inset-y-0 right-0 px-2 flex items-center" aria-hidden="true">
      <!-- Heroicon name: chevron-down -->
      <svg class="h-4 w-4 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
      </svg>
    </div>
  </div>
</template>
