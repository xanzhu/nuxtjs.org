<template>
<!--
  Tailwind UI components require Tailwind CSS v1.8 and the @tailwindcss/ui plugin.
  Read the documentation to get started: https://tailwindui.com/documentation
-->
  <footer class="bg-white">
    <div class="max-w-screen-xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
      <div class="pb-8 xl:grid xl:grid-cols-5 xl:gap-8">
        <div class="grid grid-cols-2 gap-8 xl:col-span-4">
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h4 class="text-sm leading-5 font-semibold text-gray-400 tracking-wider uppercase">
                Resources
              </h4>
              <ul class="mt-4 space-y-4">
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Design
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Themes
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Video Courses
                  </a>
                </li>
              </ul>
            </div>
            <div class="mt-12 md:mt-0">
              <h4 class="text-sm leading-5 font-semibold text-gray-400 tracking-wider uppercase">
                Support
              </h4>
              <ul class="mt-4 space-y-4">
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Sponsor NuxtJS
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    The NuxtJS Store
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    NuxtJS Consulting
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div class="md:grid md:grid-cols-2 md:gap-8">
            <div>
              <h4 class="text-sm leading-5 font-semibold text-gray-400 tracking-wider uppercase">
                Company
              </h4>
              <ul class="mt-4 space-y-4">
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    About
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Careers
                  </a>
                </li>
                <li>
                  <a href="#" class="text-base leading-6 text-gray-500 hover:text-gray-900">
                    Partners
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="mt-12 xl:mt-0">
          <h4 class="text-sm leading-5 font-semibold text-gray-400 tracking-wider uppercase">
            Language &amp; Colors
          </h4>
          <form class="mt-4 space-y-4 sm:max-w-xs">
            <fieldset class="w-full">
              <label for="language" class="sr-only">Language</label>
              <div class="relative">
                <select id="language" :value="$i18n.locale" aria-label="Languages" class="appearance-none block w-full bg-white border border-gray-300 rounded-md py-2 pl-3 pr-10 text-base leading-6 text-gray-900 focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5" @change="changeLang">
                  <option v-for="(locale, i) in $i18n.locales" :key="i" :value="locale.domain">
                    {{ locale.name }}
                  </option>
                </select>
                <div class="pointer-events-none absolute inset-y-0 right-0 px-2 flex items-center" aria-hidden="true">
                  <!-- Heroicon name: chevron-down -->
                  <svg class="h-4 w-4 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" />
                  </svg>
                </div>
              </div>
            </fieldset>
            <fieldset class="w-full">
              <label for="currency" class="sr-only">Currency</label>
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
            </fieldset>
          </form>
        </div>
      </div>
      <div class="border-t border-gray-200 pt-8 space-y-4 lg:space-y-0 lg:flex lg:items-center lg:justify-between xl:mt-0">
        <div class="space-y-2">
          <h4 class="text-sm leading-5 font-semibold text-gray-400 tracking-wider uppercase">
            Subscribe to our newsletter
          </h4>
          <p class="text-base leading-6 text-gray-500">
            The latest news, articles, and resources, sent to your inbox weekly.
          </p>
        </div>
        <form class="sm:flex sm:max-w-md">
          <label for="emailAddress" class="sr-only">Email address</label>
          <input type="email" id="emailAddress" required class="appearance-none min-w-0 w-full bg-white border border-gray-300 py-2 px-4 text-base leading-6 rounded-md text-gray-900 placeholder-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline focus:placeholder-gray-400 transition duration-150 ease-in-out sm:max-w-xs" placeholder="Enter your email">
          <div class="mt-3 rounded-md sm:mt-0 sm:ml-3 sm:flex-shrink-0">
            <button type="submit" class="w-full bg-green-500 border border-transparent rounded-md py-2 px-4 flex items-center justify-center text-base leading-6 font-medium text-white hover:bg-green-600 focus:outline-none focus:shadow-outline transition duration-150 ease-in-out">
              Subscribe
            </button>
          </div>
        </form>
      </div>
      <div class="mt-8 border-t border-gray-200 pt-8 md:flex md:items-center md:justify-between">
        <div class="flex space-x-6 md:order-2">
          <a href="#" class="text-gray-400 hover:text-gray-500">
            <span class="sr-only">Twitter</span>
            <svg class="h-6 w-6" aria-hidden="true" fill="currentColor" viewBox="0 0 24 24">
              <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84" />
            </svg>
          </a>
          <a href="#" class="text-gray-400 hover:text-gray-500">
            <span class="sr-only">GitHub</span>
            <svg class="h-6 w-6" aria-hidden="true" fill="currentColor" viewBox="0 0 24 24">
              <path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd" />
            </svg>
          </a>
          <a href="#" class="text-gray-400 hover:text-gray-500">
            <span class="sr-only">Dribbble</span>
            <svg class="h-6 w-6" aria-hidden="true" fill="currentColor" viewBox="0 0 24 24">
              <path fill-rule="evenodd" d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10c5.51 0 10-4.48 10-10S17.51 2 12 2zm6.605 4.61a8.502 8.502 0 011.93 5.314c-.281-.054-3.101-.629-5.943-.271-.065-.141-.12-.293-.184-.445a25.416 25.416 0 00-.564-1.236c3.145-1.28 4.577-3.124 4.761-3.362zM12 3.475c2.17 0 4.154.813 5.662 2.148-.152.216-1.443 1.941-4.48 3.08-1.399-2.57-2.95-4.675-3.189-5A8.687 8.687 0 0112 3.475zm-3.633.803a53.896 53.896 0 013.167 4.935c-3.992 1.063-7.517 1.04-7.896 1.04a8.581 8.581 0 014.729-5.975zM3.453 12.01v-.26c.37.01 4.512.065 8.775-1.215.25.477.477.965.694 1.453-.109.033-.228.065-.336.098-4.404 1.42-6.747 5.303-6.942 5.629a8.522 8.522 0 01-2.19-5.705zM12 20.547a8.482 8.482 0 01-5.239-1.8c.152-.315 1.888-3.656 6.703-5.337.022-.01.033-.01.054-.022a35.318 35.318 0 011.823 6.475 8.4 8.4 0 01-3.341.684zm4.761-1.465c-.086-.52-.542-3.015-1.659-6.084 2.679-.423 5.022.271 5.314.369a8.468 8.468 0 01-3.655 5.715z" clip-rule="evenodd" />
            </svg>
          </a>
        </div>
        <a href="https://url.netlify.com/B1Mh093Iv" class="mt-8 text-base leading-6 text-gray-400 md:mt-0 md:order-1">
          Deployed by Netlify
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  methods: {
    changeLang (event) {
      window.location.href = event.target.value
    }
  }
}
</script>
