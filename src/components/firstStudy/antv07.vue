<template>
  <div id="node07"></div>
</template>
<!-- 定义一个初始图形和画布 -->
<script setup>
import { onMounted } from "vue";
import { Graph } from "@antv/x6";
const data = {
  //定义节点数据
  nodes: [],
  //定义边的数据
  edges: [],
};
let graph = {};
const buildGraph = () => {
  graph = new Graph({
    container: document.getElementById("node07"),
    width: 1600,
    height: 600,
    grid: true,
    background: {
      color: "#ffbe6",
    },
    grid: {
      size: 10, //网格大小
      visible: true, //渲染网格背景
    },
  });
};
onMounted(() => {
  // console.log('jiaz');
  buildGraph();
});
</script>
<style scoped lang='scss'>
</style>
