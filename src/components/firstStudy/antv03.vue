<template>
  <div>
    <div id="node03"></div>
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
      id: "node3-1", //节点唯一标识
      shape: "rect", //矩形，也是默认值
      x: 0,
      y: 0,
      width: 80,
      height: 80,
      label: "矩形",
    },
    {
      id: "node3-2",
      shape: "circle",
      x: 100,
      y: 0,
      width: 80,
      height: 80, //按最小的一个来
      label: "圆形",
    },
    {
      id: "node3-3",
      shape: "ellipse",
      x: 250,
      y: 30,
      width: 80,
      height: 40,
      label: "椭圆形",
    },
    {
      id: "node3-4",
      shape: "polygon",
      x: 100,
      y: 150,
      width: 80,
      height: 40,
      label: "多边形",
      attrs: {
        body: {
          fill: "#efdbff",
          stroke: "#9254de",
          refPoints: "0,11 10,0 20,10 10,20",
        },
      },
    },
    {
      id: "node3-5",
      shape: "polyline",
      x: 200,
      y: 150,
      width: 80,
      height: 40,
      label: "折线",
      attrs: {
        body: {
          fill: "#efdbff",
          stroke: "#9254de",
          refPoints: "-1,2 0,5,1,15",
        },
      },
    },
    {
      id: "node3-6",
      shape: "path",
      x: 300,
      y: 150,
      width: 80,
      height: 40,
      label: "路径",
      path: "M 0 5 10 0 C 20 0 20 20 10 20 L 0 15 Z",
      attrs: {
        body: {
          fill: "#efdbff",
          stroke: "#9254de",
        },
      },
    },
    {
      id: "node3-7",
      shape: "image", //图片
      //shape:'image-bordered' 带有边框
      //shape:'image-embedded' 内嵌矩形
      //shape:'image-inscribed' 内嵌椭圆
      x: 0,
      y: 300,
      width: 80,
      height: 40,
      // label: "图片",
      imageUrl: "http://www.w3.org/2000/svg",
    },
    {
      id: "node3-8",
      shape: "text-block",
      x: 100,
      y: 300,
      width: 100,
      height: 100,
      text: "文本",
      attrs: {
        body: {
          fill: "#efdbff",
          stroke: "#fff",
          rx: 10, //圆角
          ry: 10,
        },
      },
    },
    {
      id: "node3-9",
      shape: "cylinder",
      x: 250,
      y: 300,
      width: 80,
      height: 40,
      label: "圆柱",
      attrs: {
        top: {
          fill: "red",
          stroke: "#fff",
          // fillOpacity: 0.1,
        },
        body: {
          fill: "green",
        },
      },
    },
    {
      id: "node3-10",
      shape: "html",
      x: 350,
      y: 300,
      width: 80,
      height: 80,
      // label: "html",
      html() {
        const wrap = document.createElement("div");
        // wrap.style.width = "100%";
        // wrap.style.height = "100%";
        // wrap.style.background = "skyblue";
        // wrap.style.display = "flex";
        // wrap.style.justifyContent = "center";
        // wrap.innerText = "是html";
        wrap.innerHTML = `<a href='#' class='wrapClass' >html</a>`;

        return wrap;
      },
    },
  ],
  //定义边的数据
  edges: [
    {
      shape: "edge", //普通的边，默认值
      source: "node3-1",
      target: "node3-2",
    },
    {
      shape: "double-edge", //双边
      source: "node3-3",
      target: "node3-2",
    },
    {
      shape: "shadow-edge", //阴影边
      source: "node3-1",
      target: "node3-4",
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
    container: document.getElementById("node03"),
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
