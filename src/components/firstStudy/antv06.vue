<template>
  <div>
    <button @click="test06">可编辑得文本</button>
    <button @click="test07">通过控制面板修改配置</button>
    <button @click="test08">转成JSON</button>
    <div id="node06"></div>
    <div :gutter="[16, 8]" style="padding-top: 10px">
      <div id="container"></div>
    </div>
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
const test06 = () => {
  const textBlock = new Shape.TextBlock({
    x: 300,
    y: 40,
    width: 300,
    height: 100,
    text: `编辑文本`,
    attrs: {
      label: {
        contenteditable: "true", //内容可编辑
      },
      body: {
        fill: "#efdbff",
        stroke: "#9254de",
        rx: 4,
        ry: 4,
      },
    },
  });
  graph.addNode(textBlock);
};
const test07 = () => {
  const meatdata = {
    x: 300,
    y: 200,
    width: 200,
    height: 60,
    attrs: {
      label: {
        text: "react", //文字
        fill: "blue", //文字颜色
      },
    },
    data: {
      userId: 1,
      roleId: 1,
    },
  };
  graph.addNode(meatdata);
};
const test08 = () => {
  console.log(graph.toJSON());
};
let graph = {};
onMounted(() => {
  // console.log('jiaz');
  graph = new Graph({
    container: document.getElementById("node06"),
    width: 1600,
    height: 600,
    grid: true,
  });
  graph.fromJSON(data);
});
</script>
<style scoped lang='scss'>
</style>
