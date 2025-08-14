<script setup lang="ts">
import DefaultSearchResult from "./default-search-result.vue";
import { Fa6MagnifyingGlass } from "vue-icons-plus/fa6";
</script>

<template>
  <section class="search-container">
    <div class="search-item">
      <Fa6MagnifyingGlass size="20" class="icon"></Fa6MagnifyingGlass>
      <div class="separator"></div>
      <input
        type="text"
        placeholder="Search seiyū's name in romaji or kanji, e.g., Natsuki Hanae or 夏樹花江"
      />
    </div>
  </section>
  <section class="seiyuu-cotainer">
    <DefaultSearchResult></DefaultSearchResult>
  </section>
</template>

<style scoped>
section {
  padding: 20px 30px;
}

.search-container {
  display: flex;
  gap: 10px;
}

.search-item {
  display: flex;
  border: 2px solid #333;
  border-radius: 0.25em;
  padding: 0.4em;
  padding-left: 15px;
  flex: 1;
  gap: 10px;
}

.separator {
  width: 2px;
  background-color: #333;
  border-radius: 10px;
}

.icon {
  margin-top: 1px;
}

input {
  border: none;
  outline: none;
  width: 100%;
  font-size: 1.2rem;
}
</style>
