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
  } catch {
    console.error("Can't fetch top seiyuus!");
  }
}

onMounted(() => getTopSeiyuu());
</script>

<template>
  <section class="default-search">
    <section class="welcome-container">
      <h1>Welcome to Seiyū Finder!</h1>
      <p>
        Find your favorite seiyū and discover <br />
        which animes and characters they have voiced.
      </p>
      <p>
        Powered by Jikan API. Jikan is an unofficial MyAnimeList API that
        provides open access to anime, manga, and character information.
      </p>
    </section>
  </section>
</template>

<style scoped>
.default-search {
  display: flex;
  justify-content: space-around;
}

img {
  width: 120px;
  height: auto;
}

.welcome-container {
  display: flex;
  flex-direction: column;
  margin-top: 40px;
  text-align: center;
  gap: 20px;
  width: 40%;
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
