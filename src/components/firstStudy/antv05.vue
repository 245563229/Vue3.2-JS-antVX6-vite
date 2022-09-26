<template>
  <div>
    <button @click="addNodeAndEdge">创建cell基类</button>
    <div id="node05"></div>
  </div>
</template>
<!-- 定义一个初始图形和画布 -->
<script setup>
import { onMounted } from "vue";
import { Graph, Shape } from "@antv/x6";
const data = {
  //定义节点数据
  nodes: [],
  //定义边的数据
  edges: [],
};
const addNodeAndEdge = () => {
  const rect = new Shape.Rect({
    id: "node1",
    x: 40,
    y: 40,
    width: 100,
    height: 40,
    label: "rect",
    zIndex: 2,
    attrs: {
      body: {
        stroke: "blue", //边框颜色
        fill: "skyblue", //填充颜色
      },
      label: {
        text: "reat", //文字
        fill: "#333", //文字颜色
      },
    },
  });

  const circle = new Shape.Circle({
    id: "node2",
    x: 280,
    y: 200,
    width: 60,
    height: 60,
    label: "circle",
    zIndex: 2,
  });

  const edge = new Shape.Edge({
    id: "edge1",
    source: rect,
    target: circle,
    zIndex: 1,
  });
  graph.addNode(rect);
  graph.addNode(circle);
  graph.addEdge(edge);
};

let graph = {};
onMounted(() => {
  // console.log('jiaz');
  graph = new Graph({
    container: document.getElementById("node05"),
    width: 1600,
    height: 600,
    grid: true,
  });
  graph.fromJSON(data);
});
</script>
<style scoped lang='scss'>
</style>
