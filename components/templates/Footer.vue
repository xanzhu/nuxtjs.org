<template>
  <div
    class="bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow-reverse transition-colors duration-300 ease-linear z-30 pt-4 mt-1"
  >
    <div
      class="container mx-auto py-8 px-4 sm:px-6 lg:p-8 text-center lg:text-left"
    >
      <div class="grid grid-cols-1 lg:grid-cols-6 gap-8">
        <div class="lg:col-span-4 grid sm:grid-cols-3 gap-8">
          <OrganismFooterLinks
            title="Resources"
            :links="[
              { title: 'Partners' },
              { title: 'Themes' },
              { title: 'Video courses' }
            ]"
          />
          <OrganismFooterLinks
            title="Support"
            :links="[
              { title: 'Consultancy' },
              { title: 'The Nuxt Shop' },
              { title: 'Find a Nuxt job' }
            ]"
          />
          <OrganismFooterLinks
            title="Community"
            :links="[
              { title: 'Contributors' },
              { title: 'Backers & Sponsors' },
              { title: 'Contribution guide' }
            ]"
          />
        </div>
        <OrganismFooterNewsletter class="inline-block lg:col-span-2" />
      </div>
      <div
        class="mt-8 border-t border-gray-200 dark:border-gray-600 pt-8 grid md:grid-cols-3"
      >
        <div class="flex">
          <DarkModeToggle />
        </div>
        <OrganismFooterIcons />
        <div class="text-right">
          <AppLangSelect
            :value="$i18n.locale"
            :options="$i18n.locales"
            label="Select language"
          >
            <template v-slot:icon>
              <GlobeIcon />
            </template>
          </AppLangSelect>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import GlobeIcon from '~/assets/icons/globe.svg?inline'

export default {
  components: {
    GlobeIcon
  },
  data() {
    return {
      links: {
        discover: [
          { key: this.$t('footer.links.discover.design'), to: '/design' },
          { key: this.$t('footer.links.discover.team'), to: '/team' },
          { key: this.$t('footer.links.discover.blog'), to: '/blog' }
        ],
        follow: [
          { key: 'GitHub', href: 'https://github.com/nuxt/nuxt.js' },
          { key: 'Twitter', href: 'https://twitter.com/nuxt_js' },
          { key: 'Discord', href: 'https://discord.nuxtjs.org' }
        ],
        support: [
          {
            key: this.$t('footer.links.support.sponsorNuxt'),
            to: this.localePath('/sponsor-nuxtjs')
          },
          {
            key: this.$t('footer.links.support.shop'),
            to: this.localePath('/shop')
          },
          {
            key: this.$t('footer.links.support.consulting'),
            to: this.localePath('/support')
          }
        ]
      }
    }
  }
}
</script>
