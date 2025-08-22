<script setup lang="ts">
const menuList = ref(Array(100).fill(0).map((_, i) => `Menu ${i + 1}`))
const contentList = ref(Array(100).fill(0).map((_, i) => `Content ${i + 1}`))
</script>

<template>
  <main class="flex h-dvh flex-col">
    <header class="shrink-0 space-x-2 bg-red-200 py-5">
      <UButton to="/sidebar-left">
        Sidebar Left Page
      </UButton>
      <UButton to="/sidebar-top">
        Sidebar Top Page
      </UButton>
    </header>

    <!--
    原因在于 flex 的“自动最小尺寸”。

    - 默认行为：你的 main 是 flex-col，section 作为它的子项且有 flex-1。在这种纵向主轴里，flex 子项的默认
    min-height: auto 会按“内容最小高度”计算，也就是“至少要能装下里面的内容”。当 aside 很高时，section 会被
    它的内容最小高度“撑大”，不愿意收缩到视口剩余高度。
    束，overflow-y-auto 自然不生效（元素要有明确高度/上限才会出现内部滚动条）。
    - 加上 min-h-0: 把 section 的“自动最小高度”关掉，允许它收缩到可用高度（= 100dvh - header）。section
    有了确定高度后，内部横向 flex 的子项（aside 和右侧内容）会按默认对齐拉伸到同样的高度，这时 aside 的
    overflow-y-auto 就会按预期只在左侧出现滚动。
    -->
    <section class="flex min-h-0 flex-1">
      <aside class="w-60 shrink-0 overflow-y-auto bg-amber-100">
        <ul>
          <li
            v-for="item in menuList"
            :key="item"
          >
            {{ item }}
          </li>
        </ul>
      </aside>
      <div class="min-w-0 flex-1 overflow-y-auto bg-blue-300">
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
