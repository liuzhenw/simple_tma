<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <TonConnect />
  <HelloWorld msg="Hello TWA!" />
  <p>TWA version:{{ version }}</p>
  <P>Init Data:{{ initData }}</P>
</template>

<script setup>
import eruda from "eruda";
import WebApp from "@twa-dev/sdk";
import HelloWorld from "./components/HelloWorld.vue";
import TonConnect from "./components/TonConnect.vue";
import { ref } from "vue";
eruda.init();

const version = ref(WebApp.version);
const initData = ref(WebApp.initDataUnsafe);
WebApp.ready();
if (!WebApp.isExpanded) WebApp.expand();
WebApp.MainButton.setParams({
  text: "START",
  is_active: true,
  is_visible: true,
});
WebApp.MainButton.onClick(() => {
  //WebApp.showAlert("Hello TWA!");
  WebApp.sendData("Hello TWA!");
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
