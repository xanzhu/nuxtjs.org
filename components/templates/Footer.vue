<template>
  <div
    class="bg-light-elevatedSurface dark:bg-dark-elevatedSurface shadow-nuxt transition-colors duration-300 ease-linear"
  >
    <div class="max-w-screen-xl mx-auto py-12 px-4 sm:px-6 lg:py-16 lg:px-8">
      <div class="grid md:grid-cols-2 xl:grid-cols-4 md:gap-12 xl:gap-0">
        <OrganismFooterLinks
          title="Resources"
          :links="[
            { title: 'Partners' },
            { title: 'Themes' },
            { title: 'Video courses' }
          ]"
        />
        <OrganismFooterLinks
          class="mt-12 md:mt-0"
          title="Support"
          :links="[
            { title: 'Consultancy' },
            { title: 'The Nuxt Shop' },
            { title: 'Find a Nuxt job' }
          ]"
        />
        <OrganismFooterLinks
          class="mt-12 md:mt-0"
          title="Community"
          :links="[
            { title: 'Contributors' },
            { title: 'Backers & Sponsors' },
            { title: 'Contribution guide' }
          ]"
        />
        <OrganismFooterNewsletter class="mt-12 md:mt-0" />
      </div>
      <div class="mt-8 border-t border-gray-200 pt-8 grid md:grid-cols-3">
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
