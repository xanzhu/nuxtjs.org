<template>
  <div>
    <h4
      class="text-sm leading-5 font-semibold tracking-wider text-gray-400 uppercase"
    >
      {{ title }}
    </h4>
    <ul class="mt-4">
      <li v-for="(link, i) in links" :key="i" :class="{ 'mt-4': i > 0 }">
        <a
          href="#"
          class="text-base leading-6 text-gray-500 hover:text-gray-900"
        >
          {{ link.title }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    links: {
      type: Array,
      required: true
    }
  }
}
</script>
