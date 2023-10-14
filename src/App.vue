<script setup lang="ts">
import ResizeableWindow from './components/ResizeableWindow.vue'

const top = `calc(50% - ${500 / 2}px)`
const left = `calc(50% - ${500 / 2}px)`
</script>

<template>
  <div class="w-screen h-screen">
    <ResizeableWindow style="position: absolute" :top="top" :left="left" :height="500" :width="500">
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsam a corrupti, doloribus
        consequuntur vero suscipit saepe quam eius ullam porro veniam distinctio atque quas facere,
        nihil eaque? Deleniti, reprehenderit. Eveniet!
      </p>
    </ResizeableWindow>
  </div>
</template>

<style scoped></style>
