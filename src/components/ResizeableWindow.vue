<script setup lang="ts">
import VueResizable from 'vue-resizable'

import { ref } from 'vue'
const props = defineProps<{
  top: String
  left: String
  height: Number
  width: Number
}>()

const w = ref(props.width)
const h = ref(props.height)
const t = ref(props.top)
const l = ref(props.left)
const dragSelector = ref('.drag-handle-top')
const handles = ref(['r', 'rb', 'b', 'lb', 'l', 'lt', 't', 'rt'])

function updates(data: any) {
  w.value = data.width
  h.value = data.height
  t.value = data.top
  l.value = data.left
}
</script>

<template>
  <vue-resizable
    class="resizable overflow-hidden"
    ref="resizableComponent"
    :dragSelector="dragSelector"
    :active="handles"
    :fit-parent="true"
    :width="w"
    :height="h"
    :left="l"
    :top="t"
    :min-width="200"
    :min-height="200"
    @mount="updates"
    @resize:move="updates"
    @resize:start="updates"
    @resize:end="updates"
    @drag:move="updates"
    @drag:start="updates"
    @drag:end="updates"
    @maximize="updates"
  >
    <div class="block">
      <div class="drag-handle-top flex justify-between items-center">
        <div>Title</div>
        <div>
          <button class="px-2">-</button>
          <button class="px-2">X</button>
        </div>
      </div>
      <div class="table-container">
        <table>
          <tr>
            <td>w:{{ w }}</td>
            <td>h:{{ h }}</td>
          </tr>
          <tr>
            <td>l:{{ l }}</td>
            <td>t:{{ t }}</td>
          </tr>
        </table>
      </div>
    </div>
  </vue-resizable>
</template>
<style>
.resizable {
  padding: 0;
  border: 1px solid #003eff;
  background: #007fff;
  font-weight: normal;
  color: #ffffff;
  position: relative;
}

.block {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.container {
  width: 300px;
  height: 300px;
  display: inline-block;
  border: 1px solid #dddddd;
  background: #ffffff;
  color: #333333;
  margin: 10px;
}

.drag-handle-top {
  width: 100%;
  height: 40px;
  background: rgb(218, 159, 159);
  color: rgb(0, 0, 0);
  cursor: pointer;
}

.table-container {
  flex: 1;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
