<template>
  <div>
    <h4
      class="text-sm leading-5 font-semibold tracking-wider text-gray-400 uppercase"
    >
      Subscribe to our newsletter
    </h4>
    <p class="mt-4 text-gray-500 text-base leading-6">
      <span v-if="subscribed" class="text-green-500">
        {{ $t('homepage.newsletter.form.subscribed_messages.pre') }}
        {{ subscribedEmail }}
        {{ $t('homepage.newsletter.form.subscribed_messages.post') }}
      </span>
      <span v-else-if="error" class="text-red-600 py-1">
        {{ error }}
      </span>
      <span v-else>
        {{ $t('homepage.newsletter.description') }}
      </span>
    </p>
    <ClientOnly>
      <form
        class="relative mt-4 flex sm:max-w-md"
        data-cy="newsletter"
        @submit.prevent="subscribe"
      >
        <label for="news-email" class="hidden">
          {{ $t('homepage.newsletter.form.email') }}
        </label>
        <input
          id="news-email"
          v-model="email"
          type="email"
          required
          :placeholder="'Enter your ' + $t('homepage.newsletter.form.email')"
          aria-label="Newsletter"
          class="appearance-none w-full px-3 py-3 pr-32 border border-gray-300 text-base leading-6 rounded-md text-gray-900 bg-white placeholder-gray-500 focus:outline-none focus:placeholder-gray-400 focus:border-blue-300 focus:shadow-outline transition duration-150 ease-in-out"
        />
        <div class="absolute p-1 right-0 mt-0 flex-shrink-0">
          <input
            type="submit"
            :value="
              pending
                ? $t('homepage.newsletter.form.subscribing')
                : $t('homepage.newsletter.form.subscribe')
            "
            name="subscribe"
            class="w-full flex items-center justify-center px-4 py-2 border border-transparent text-base leading-6 font-medium rounded-md text-white bg-nuxt-lightgreen hover:bg-nuxt-green focus:outline-none focus:shadow-outline cursor-pointer transition duration-150 ease-in-out"
          />
        </div>
      </form>
    </ClientOnly>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      subscribedEmail: '',
      pending: false,
      subscribed: false,
      error: null
    }
  },
  methods: {
    async subscribe() {
      if (!this.email.trim()) {
        return
      }
      this.error = null
      this.pending = true
      try {
        await new Promise(resolve => setTimeout(resolve, 400))
        await this.$http.$post(`${process.env.NUXT_API}/newsletter`, {
          email: this.email
        })
        this.subscribedEmail = this.email
        this.subscribed = true
        this.pending = false
      } catch (err) {
        this.pending = false
        if (err.response) {
          const { code } = await err.response.json()
          if (code === 'member-exists') {
            this.error = 'You are already registered.'
            return
          }
        }
        this.error = 'Unknown error'
      }
    }
  }
}
</script>
