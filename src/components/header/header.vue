<script setup lang="ts">
const props = defineProps<{
  changeMainComponent: (index: number) => void;
}>();
</script>

<template>
  <header>
    <h1>Seiyū Finder</h1>
    <nav>
      <ul>
        <li @click="props.changeMainComponent(0)">Home</li>
        <li @click="props.changeMainComponent(1)">What is Seiyū?</li>
        <li @click="props.changeMainComponent(2)">About This Project</li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-inline: 30px;
  padding-block: 20px;
  font-family: "Montserrat", sans-serif;
  color: #333;
  border-bottom: 2px solid #333;
}

h1 {
  font-family: inherit;
  font-size: 1.5rem;
  font-weight: bold;
}

ul {
  display: flex;
  font-family: inherit;
  gap: 30px;
}

li {
  font-size: 1.1rem;
  font-weight: 500;
  color: inherit;
  text-decoration: none;
  text-underline-offset: 4px;
  cursor: pointer;
}

li:hover {
  text-decoration: underline;
}
</style>
