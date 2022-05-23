<script setup lang="ts">
import { Viewer, ArcGisMapServerImageryProvider } from "cesium";
import * as Cesium from "cesium";

onMounted(() => {
  const option = {
    geocoder: false, // 地理编码（搜索）组件
    homeButton: false, // 首页，点击之后将视图跳转到默认视角
    sceneModePicker: false, // 场景模式，切换2D、3D 和 Columbus View (CV) 模式。
    baseLayerPicker: true, // 底图组件，选择三维数字地球的底图（imagery and terrain）。
    navigationHelpButton: false, // 帮助提示，如何操作数字地球。
    animation: false, // 动画小组件
    timeline: false, // 时间轴
    fullscreenButton: false, // 全屏组件
    //
    vrButton: false, // VR模式
    infoBox: false, // 信息框
    // imageryProviderViewModels: [], //BaseLayerPicker 选择的图层数组
    // imageryProvider: undefined, // 默认选中的图层baseLayerPicker 为false有效
    selectionIndicator: false, //是否显示选取指示器组件
    // 如果最初应该看到导航说明，则为true；如果直到用户明确单击该按钮，则该提示不显示，否则为false。
    navigationInstructionsInitiallyVisible: false,

    // 地形
    selectedTerrainProviderViewModel: undefined, //当前地形图层的显示模型，仅 baseLayerPicker 设为true 有意义
    terrainProviderViewModels: [], // 可 供BaseLayerPicker 选择的地形图层 ProviderViewModel 数组
    terrainProvider: new Cesium.EllipsoidTerrainProvider(), //地形图层提供者，仅 baseLayerPicker 设为false 有意义
  };
  const viewer = new Viewer("cesiumContainer", option);

  // 隐藏logo
  // @ts-ignore
  viewer._cesiumWidget._creditContainer.style.display = "none";
});
</script>

<template>
  <div id="cesiumContainer"></div>
</template>

<style>
html,
body,
#app,
#cesiumContainer {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
