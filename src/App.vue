<template>
  <nav class="flex bg-zinc-900 text-white p-4 items-center justify-center gap-4">
    <router-link class="hover:bg-blue-700 rounded-xl p-2" to="/">Home</router-link> |
    <router-link class="hover:bg-blue-700 rounded-xl p-2" to="/about">About</router-link>
  </nav>
  <router-view/>
</template>

