<template>
  <header
    class="sticky top-0 z-50 text-sm font-medium text-white bg-gray-900 border-b border-gray-800/75"
  >
    <div class="container flex items-center justify-between h-16">
      <nav class="hidden sm:items-center sm:space-x-8 sm:flex">
        <nuxt-link :to="{ name: 'index' }">
          Gradients
        </nuxt-link>

        <nuxt-link
          v-for="{ title, name } in navigation"
          :key="name"
          :to="{ name }"
          v-text="title"
        />
      </nav>

      <div class="hidden sm:items-center sm:flex sm:space-x-8">
        <header-jordi class="hidden sm:block" />
        <header-mark class="hidden sm:block" />
        <header-github />
      </div>

      <nuxt-link :to="{ name: 'index' }" class="block sm:hidden">
        Gradients
      </nuxt-link>

      <button
        type="button"
        class="inline-block sm:hidden p-2.5 rounded-xl bg-gray-800/75"
        @click="toggleMobile"
      >
        <icons-menu class="w-4 h-4" />
      </button>
    </div>

    <div v-if="mobile" class="absolute z-50 w-full p-4">
      <div class="p-8 bg-gray-900 ring-2 ring-pink-500 rounded-xl">
        <nav class="flex flex-col items-center space-y-4">
          <nuxt-link
            v-for="{ title, name } in navigation"
            :key="name"
            :to="{ name }"
            v-text="title"
          />
        </nav>

        <div class="flex items-center justify-center mt-8 space-x-8">
          <header-jordi />
          <header-mark />
          <header-github />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
/* eslint-disable space-before-function-paren */

import { navigation } from '@/assets/data/navigation'

export default {
  data() {
    return {
      mobile: false
    }
  },
  computed: {
    navigation() {
      return navigation
    }
  },
  watch: {
    $route() {
      this.mobile = false
    }
  },
  methods: {
    toggleMobile() {
      this.mobile = !this.mobile
    }
  }
}
</script>
