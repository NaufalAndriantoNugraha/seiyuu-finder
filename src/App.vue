<script setup lang="ts">
import Header from "./components/header/header.vue";
import HeaderSeparator from "./components/separator/header-separator.vue";
import Home from "./components/main/home.vue";
import WhatIsSeiyuu from "./components/main/what-is-seiyuu.vue";
import AboutThisProject from "./components/main/about-this-project.vue";
import { ref } from "vue";

const currentComponentIndex = ref<number>(0);
const componentList = [
  { id: 0, component: Home },
  { id: 1, component: WhatIsSeiyuu },
  { id: 2, component: AboutThisProject },
];

function setCurrentComponentIndex(index: number) {
  currentComponentIndex.value = index;
}

function setCurrentComponent() {
  return componentList.find(
    (component) => component.id === currentComponentIndex.value,
  )?.component;
}
</script>

<template>
  <Header :change-main-component="setCurrentComponentIndex"></Header>
  <HeaderSeparator></HeaderSeparator>
  <component :is="setCurrentComponent()" :key="currentComponentIndex" />
</template>

<style scoped></style>
