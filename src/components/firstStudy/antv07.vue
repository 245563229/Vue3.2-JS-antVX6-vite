<template>
  <div id="node07"></div>
</template>
<!-- 定义一个初始图形和画布 -->
<script setup>
import { onMounted } from "vue";
import { Graph } from "@antv/x6";
const data = {
  //定义节点数据
  nodes: [
    {
      id: "node1-1", //节点唯一标识
      x: 0,
      y: 0,
      width: 80,
      height: 80,
      label: "节点1",
    },
    {
      id: "node1-2",
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
      source: "node1-1",
      target: "node1-2",
    },
  ],
};
let graph = {};
onMounted(() => {
  // console.log('jiaz');
  graph = new Graph({
    container: document.getElementById("node07"),
    width: 1600,
    height: 600,
    grid: true,
  });
  graph.fromJSON(data);
});
</script>
<style scoped lang='scss'>
</style>
