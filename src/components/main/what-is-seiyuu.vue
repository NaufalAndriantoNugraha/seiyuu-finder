<script setup lang="ts"></script>

<template>
  <main>
    <figure>
      <div class="images">
        <img
          src="../../assets/Natsuki_Hanae.jpg"
          alt="Picture of Natsuki Hanae"
        />
        <img
          src="../../assets/Yoshitsugu_Matsuoka_松岡_禎丞_2022.jpg"
          alt="Picture of Matsuoka Yoshitsugu"
        />
        <img src="../../assets/Kito_Akari.jpg" alt="Picture of Kito Akari" />
        <img
          src="../../assets/Hiro_Shimono.jpg"
          alt="Picture of Shimono Hiro"
        />
      </div>
      <figcaption>
        Pictures of Natsuki Hanae, Matsuoka Yoshitsugu, Kito Akari, and Simono
        Hiro (from left to right) who are famous seiyū.
      </figcaption>
    </figure>
    <h1>What is Seiyū?</h1>
    <p>
      声優 (seyū or seiyuu) is the Japanese word for voice actor or voice
      actress. Seiyū provides voice-overs for characters and narration for
      various types of media, including anime, video games, audio dramas,
      live-action stunt, puppet shows, and commercials.
    </p>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 5%;
  height: 100%;
  gap: 20px;
}

figure {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  margin-bottom: 20px;
}

.images {
  display: flex;
  justify-content: center;
  gap: 8px;
}

img {
  width: 130px;
  height: auto;
}

figcaption {
  width: 55%;
  text-align: center;
  font-size: 0.8rem;
  font-family: "Noto Sans JP", sans-serif;
  letter-spacing: 1px;
}

h1 {
  font-family: "Montserrat", sans-serif;
  font-weight: bold;
  font-size: 1.6rem;
}

p {
  font-family: "Noto Sans JP", sans-serif;
  font-size: 1.1rem;
  width: 40%;
  text-align: justify;
  letter-spacing: 1px;
  line-height: 2;
}
</style>
