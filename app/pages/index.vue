<script setup lang="ts">
const menuList = ref(Array(100).fill(0).map((_, i) => `Menu ${i + 1}`))
const contentList = ref(Array(100).fill(0).map((_, i) => `Content ${i + 1}`))
</script>

<template>
  <main class="flex h-dvh">
    <aside class="w-60 shrink-0 overflow-y-auto border-r border-gray-200 p-5">
      <ul class="space-y-2">
        <li
          v-for="value in menuList"
          :key="value"
        >
          {{ value }}
        </li>
      </ul>
    </aside>

    <section class="flex min-w-0 flex-1 flex-col">
      <header class="shrink-0 border-b border-gray-200 p-5">
        header
      </header>

      <div
        class="
          m-5 min-h-0 flex-1 overflow-y-auto rounded-xl bg-gray-200 p-3
          dark:bg-gray-700
        "
      >
        <ul class="space-y-2">
          <li
            v-for="value in contentList"
            :key="value"
          >
            {{ value }}
          </li>
        </ul>
      </div>
    </section>
  </main>
</template>
