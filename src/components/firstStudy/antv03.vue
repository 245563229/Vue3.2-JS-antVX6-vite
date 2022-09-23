<template>
  <div>
    <div style="width: 400px; height: 30px; z-index: 555">
      <button @click="translate">平移</button>
      <button @click="reduce">缩小0.5</button>
      <button @click="zoom">放大0.5</button>
    </div>
    <div id="node02"></div>
  </div>
</template>
<!-- 13种内置节点和3种内置边 -->
<script setup>
import { onMounted } from "vue";
import { Graph } from "@antv/x6";
const data = {
  //定义节点数据
  nodes: [
    {
      id: "node2-1", //节点唯一标识
      x: 0,
      y: 0,
      width: 80,
      height: 80,
      label: "节点1",
    },
    {
      id: "node2-2",
      x: 300,
      y: 100,
      width: 80,
      height: 80,
      label: "节点2",
    },
  ],
  //定义边的数据
  edges: [
    {
      source: "node2-1",
      target: "node2-2",
    },
  ],
};
const translate = () => {
  graph.translate(80, 40);
};
const reduce = () => {
  graph.zoom(-0.5);
};
const zoom = () => {
  graph.zoom(0.5);
};
let graph = {};
onMounted(() => {
  // console.log('jiaz');
  graph = new Graph({
    container: document.getElementById("node02"),
    width: 1600,
    height: 600,
    grid: true,
    background: {
      color: "#fffbe6",
    },
  });
  graph.fromJSON(data);
});
</script>
<style scoped lang='scss'>
</style>
