<script setup lang="ts">
import axios from "axios";
import { onMounted, ref } from "vue";

type TopSeiyuu = {
  name: string;
};

const topSeiyuuList = ref<Array<TopSeiyuu>>([]);

async function getTopSeiyuu() {
  try {
    const response = await axios.get(
      "https://api.jikan.moe/v4/top/people?limit=6",
    );
    const seiyuus = await response.data.data;
    for (let i = 0; i < 6; i++) {
      const seiyuu: TopSeiyuu = {
        name: seiyuus[i]["name"],
      };
      topSeiyuuList.value.push(seiyuu);
    }
    console.log(topSeiyuuList);
  } catch {
    console.error("Can't fetch top seiyuus!");
  }
}

onMounted(() => getTopSeiyuu());
</script>

<template>
  <section>
    <div class="welcome-container">
      <h1>Welcome, to Seiyū Finder!</h1>
      <p>
        Find your favorite seiyū and discover <br />
        which animes and characters they have voiced.
      </p>
    </div>
    <div class="top-seiyuu-cotainer">
      <h2>Top 6 Seiyūs right now</h2>
      <div class="list">
        <ol>
          <li v-for="seiyuu in topSeiyuuList">
            {{ seiyuu["name"] }}
          </li>
        </ol>
      </div>
    </div>
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
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
  text-align: center;
  letter-spacing: 1px;
  line-height: 1.5;
}

.list {
  display: flex;
}

.welcome-container,
.top-seiyuu-cotainer {
  display: flex;
  flex-direction: column;
}

.welcome-container {
  align-items: center;
  width: 40%;
}

.top-seiyuu-cotainer {
  align-items: center;
  gap: 20px;
  border: 1px solid #333;
  border-radius: 4px;
  padding: 20px 50px;
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
