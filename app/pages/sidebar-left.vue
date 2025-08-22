<script setup lang="ts">
const menuList = ref(Array(100).fill(0).map((_, i) => `Menu ${i + 1}`))
const contentList = ref(Array(100).fill(0).map((_, i) => `Content ${i + 1}`))
</script>

<template>
  <main class="flex h-dvh">
    <aside class="w-60 overflow-y-auto bg-amber-100">
      <ul>
        <li
          v-for="item in menuList"
          :key="item"
        >
          {{ item }}
        </li>
      </ul>
    </aside>

    <section class="flex min-w-0 flex-1 flex-col">
      <header class="shrink-0 space-x-2 bg-red-200 py-5">
        <UButton to="/sidebar-left">
          Sidebar Left Page
        </UButton>
        <UButton to="/sidebar-top">
          Sidebar Top Page
        </UButton>
      </header>

      <div class="min-h-0 flex-1 overflow-y-auto bg-blue-300">
        <ul>
          <li
            v-for="item in contentList"
            :key="item"
          >
            {{ item }}
          </li>
        </ul>
      </div>
    </section>
  </main>
</template>
