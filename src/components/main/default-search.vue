<script setup lang="ts">
import axios from "axios";
import { onMounted, ref } from "vue";

type TopSeiyuu = {
  name: string;
  img: string;
};

const topSeiyuuList = ref<Array<TopSeiyuu>>([]);

async function getTopSeiyuu() {
  try {
    const response = await axios.get(
      "https://api.jikan.moe/v4/top/people?limit=6",
    );
    const seiyuus = await response.data.data;
    for (let seiyuu of seiyuus) {
      const newSeiyuu: TopSeiyuu = {
        name: seiyuu.name,
        img: seiyuu.images.jpg.image_url,
      };
      topSeiyuuList.value.push(newSeiyuu);
    }
    console.log(topSeiyuuList);
  } catch {
    console.error("Can't fetch top seiyuus!");
  }
}

onMounted(() => getTopSeiyuu());
</script>

<template>
  <section class="default-search">
    <section class="welcome-container">
      <div class="welcome-message">
        <h1>Welcome to Seiyū Finder!</h1>
        <p>
          Find your favorite seiyū and discover <br />
          which animes and characters they have voiced.
        </p>
      </div>
      <div class="top-seiyuu-cotainer">
        <h2>Top 6 seiyūs right now</h2>
        <div class="list">
          <ol>
            <li v-for="seiyuu in topSeiyuuList">
              {{ seiyuu["name"] }}
            </li>
          </ol>
        </div>
      </div>
    </section>
    <section class="seiyuu-preview">
      <img
        v-for="seiyuu in topSeiyuuList"
        :src="seiyuu?.img"
        :alt="seiyuu?.name"
      />
    </section>
  </section>
</template>

<style scoped>
.default-search {
  display: flex;
  justify-content: space-around;
}

.seiyuu-preview {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

img {
  width: 120px;
  height: auto;
}

.welcome-container {
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  gap: 40px;
}

h1 {
  font-family: "Montserrat", sans-serif;
  font-size: 1.8rem;
  font-weight: bold;
  margin-bottom: 15px;
}

p {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 1.15rem;
  letter-spacing: 1px;
  line-height: 1.5;
}

.list {
  display: flex;
}

.welcome-message {
  display: flex;
  flex-direction: column;
}

.top-seiyuu-cotainer {
  display: flex;
  flex-direction: column;
  gap: 20px;
  border-radius: 4px;
}

h2 {
  font-family: "Montserrat", sans-serif;
  font-size: 1.25rem;
  font-weight: bold;
}

ol {
  columns: 2;
  list-style-position: inside;
  font-family: "Noto Sans JP", sans-serif;
  letter-spacing: 1px;
}

li {
  margin-bottom: 4px;
}
</style>
