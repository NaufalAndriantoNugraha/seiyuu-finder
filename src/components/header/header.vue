<script setup lang="ts"></script>

<template>
  <header>
    <h1>Seiyū Finder</h1>
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">What is Seiyū?</a></li>
        <li><a href="#">About This Project</a></li>
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

a {
  font-size: 1.1rem;
  font-weight: 500;
  color: inherit;
  text-decoration: none;
  text-underline-offset: 4px;
}

a:hover {
  text-decoration: underline;
}
</style>
