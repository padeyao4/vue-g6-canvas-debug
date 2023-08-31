<script setup lang="ts">
import { Graph } from '@antv/g6';
import { onMounted, ref } from 'vue';

let container = ref<HTMLElement>()
let graph = ref<Graph>()

onMounted(() => {
  graph.value = new Graph({
    container: container.value!
  })
  graph.value.on('canvas:click', () => {
    alert('canvas click')
  })
})

const handlerChangeSize = () => {
  graph.value?.changeSize(container.value!.clientWidth, container.value!.clientHeight)
}

const handleRender=()=>{
  graph.value?.render()
}

</script>

<template>
  <div style="display: flex;">
    <button @click="handlerChangeSize">change-size</button>
    <button @click="handleRender">render</button>
  </div>
  <fieldset style="width: 400px;height: 400px;">
    <div ref="container" style="width: 100%;height: 100%; border: 1px black;"></div>
  </fieldset>
</template>