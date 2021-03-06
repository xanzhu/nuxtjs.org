<template>
  <div class="-mx-4 lg:mx-0 flex flex-col-reverse lg:flex-row">
    <div
      class="w-full py-8 px-4 lg:static lg:overflow-visible lg:max-h-full lg:w-3/4"
    >
      <article>
        <h1 class="text-light-onSurfacePrimary dark:text-dark-onSurfacePrimary transition-colors duration-300 ease-linear">
          {{ page.title }}
        </h1>
        <AppResponsiveVideo v-if="page.youtube" :src="page.youtube" />
        <nuxt-content :document="page" />
        <AppContribute :doc-link="docLink" :contributors="contributors" />
      </article>
    </div>
    <AffixBlock>
      <SponsorsBlock />
      <AdsBlock :key="$route.params.slug" />
    </AffixBlock>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, store, error, app }) {
    const slug = params.slug || 'external-resources'

    let path = `/${app.i18n.defaultLocale}/faq`
    let page, prev, next, contributors, langFallback

    try {
      page = await $content(path, slug).fetch()
    } catch (err) {
      return error({
        statusCode: 404,
        message: app.i18n.t('common.page_not_found')
      })
    }

    if (app.i18n.defaultLocale !== app.i18n.locale) {
      try {
        path = `/${app.i18n.locale}/faq`
        page = await $content(path, slug).fetch()
      } catch (err) {
        langFallback = true
        path = `/${app.i18n.defaultLocale}/faq`
      }
    }

    try {
      contributors = (
        await fetch(
          `https://contributors-api.onrender.com/content${path}/${slug}`
        ).then(res => res.json())
      ).map(({ author }) => ({ author }))
    } catch (e) {}

    try {
      ;[prev, next] = await $content(path)
        .only(['title', 'slug', 'dir'])
        .sortBy('position')
        .surround(slug, { before: 1, after: 1 })
        .fetch()
    } catch (e) {}

    return {
      langFallback,
      path,
      section: params.section,
      page,
      prev,
      next,
      contributors
    }
  },
  computed: {
    docLink() {
      return `https://github.com/nuxt/nuxtjs.org/blob/master/content${this.path}.md`
    }
  },
  scrollToTop: true,
  head() {
    return {
      title: this.page.title,
      titleTemplate: '%s - NuxtJS',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.page.description
        },
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: this.page.title },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.page.description
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.page.title
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.page.description
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
article h1 {
  @apply font-medium relative text-3xl table mb-8;

  &::after {
    content: ' ';
    width: 80%;

    @apply block border-2 border-nuxt-lightgreen mt-2 mb-1 rounded;
  }
}
</style>
