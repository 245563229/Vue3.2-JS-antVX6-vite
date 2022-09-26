<template>
  <div>
    <button @click="enablePanning">启动画布平移(shift+左键)</button>
    <button @click="disablePanning">关闭画布平移</button>
    <button @click="panningStatus">画布平移状态</button>
    <button @click="togglePanning">切换画布平移状态</button>
    <button @click="getZoom">获取缩放比例</button>
    <button @click="zoomAdd">缩放原来基础上+0.2</button>
    <button @click="zoomReduce">缩放原来基础上-0.2</button>
    <button @click="centerContent">画布中心与视口中心对齐</button>
    <button @click="toSVG">导出SVG</button>
    <button @click="toPNG">导出PNG</button>
    <button @click="dispose">销毁画布</button>
    <div id="node04"></div>
  </div>
</template>
<!-- 13种内置节点和3种内置边 -->
<script setup>
import { onMounted } from "vue";
import { Graph, DataUri } from "@antv/x6";

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
      shape: "ellipse",
      x: 0,
      y: 150,
      width: 80,
      height: 40,
      label: "椭圆形",
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
let graph = {};
onMounted(() => {
  // console.log('jiaz');
  graph = new Graph({
    container: document.getElementById("node04"),
    width: 1600,
    height: 600,
    grid: true,
    // panning: true, //平移属性
    panning: {
      enabled: true, // 开启平移属性写法2
      modifiers: "shift", //需要按住shitf
    },
    background: {
      color: "#fffbe6",
    },
  });
  graph.fromJSON(data);
  //启动画布平移
});
const enablePanning = () => {
  graph.enablePanning();
};
const disablePanning = () => {
  graph.disablePanning();
};
const panningStatus = () => {
  console.log(graph.isPannable());
};
const togglePanning = () => {
  graph.togglePanning();
};
const getZoom = () => {
  console.log(graph.zoom());
};
const zoomAdd = () => {
  graph.zoom(0.2);
};
const zoomReduce = () => {
  graph.zoom(-0.2);
};
const centerContent = () => {
  graph.centerContent();
};
const toSVG = () => {
  graph.toSVG(
    (dataUri) => {
      DataUri.downloadDataUri(DataUri.svgToDataUrl(dataUri), "chart.svg");
    },
    {
      preserveDimensions: {
        width: 200,
        height: 200,
      },
      stylesheet: `
    rect {
      fill: red;
    }
  `,
    }
  );
};
const toPNG = () => {
  graph.toPNG(
    (dataUri) => {
      DataUri.downloadDataUri(dataUri, "chart.png");
    },
    {
      backgroundColor: "red",
      quality: 1, //图片质量
    }
  );
};
const dispose = () => {
  graph.dispose();
};
</script>
<style scoped lang='scss'>
#antv04Vue {
  width: 100%;
}
</style>
