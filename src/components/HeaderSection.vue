<script lang="ts">
import { ref } from 'vue'

export default {
  setup() {
    let open = ref(false)
    let Links = [
      { name: 'Home', link: '/' },
      // { name: 'Services', link: '/talks' },
      // { name: 'About', link: '/about' },
      { name: 'Contact', link: '/contact' }
    ]
    let signLinks = [
      { name: 'Log In', link: '/login' },
      { name: 'Sign Up', link: '/register' },
      { name: 'Profile', link: '/dashboard' }
    ]

    // change value for menu icon
    function menuOpen() {
      open.value = !open.value
    }

    return { Links, signLinks, open, menuOpen }
  }
}
</script>
<template>
  <nav class="bg-blue-200 pt-2 top-0 left-0 w-full flex justify-between mb-3">
    <div class="z-30 content-center">
      <!-- Logo -->
      <div class="flex content-center items-center">
        <img src="@/assets/img/logo.png" alt="" class="h-18 w-24" />
        <h1 class="text-2xl text-black md:max-w-20">cancerHub Center</h1>
      </div>
      <!-- Nav bar icon-->
      <span
        @click="menuOpen()"
        class="absolute md:hidden right-5 top-2 cursor-pointer text-5xl text-black"
      >
        <i :class="[open ? 'bi bi-x' : 'bi bi-filter-left']"></i>
      </span>
    </div>

    <div
      class="h-screen md:h-max absolute md:static bg-blue-200 w-full md:w-max flex flex-col content-center md:flex-row md:gap-6 pt-20 md:pt-2"
      :class="[open ? 'left-0' : 'left-[-100%]']"
    >
      <ul class="list-none md:flex">
        <li class="text-center p-3" v-for="link in Links" :key="link.name">
          <a
            class="text-black text-xl font-semibold hover:underline hover:text-orange-500"
            :href="link.link"
            >{{ link.name }}</a
          >
        </li>
      </ul>
      <div
        class="text-center pt-5 flex flex-col md:flex-row justify-center gap-4 text-black text-xl"
      >
        <button v-for="link in signLinks" :key="link.name">
          <a :href="link.link" class="font-semibold hover:underline hover:text-orange-500">{{
            link.name
          }}</a>
        </button>
      </div>
    </div>
  </nav>
</template>
