<template>
  <game-heading v-slot:AnimalLandTitle>
    <h3 class="text-center pt-2 fw-bolder">Mombosa</h3>
  </game-heading>
  <div class="container px-5 mt-4 mb-5">
    <div class="row gap-5">
      <div
        id="animalCard"
        class="col justify-content-center align-items-center cardShadow"
        v-for="animal in animalLand"
        :key="animal.id"
        @click="playAnimalSound(animal)"
      >
        <img :src="animal.imageSrc" alt="loading..." />
      </div>
    </div>
  </div>
</template>
<script>
import { animalLand } from "../assets/gameData";
import clickSoundSrc from "../assets/audio/click.wav";
import GameHeading from "./GameHeading.vue";

export default {
  name: "Animal Land",
  components: {
    GameHeading,
  },
  data() {
    return {
      animalLand: animalLand,
      isPlaying: false,
      audio: null,
      clickSound: null,
    };
  },
  mounted() {
    this.clickSound = new Audio(clickSoundSrc);
  },
  methods: {
    playAnimalSound(animal) {
      // Check if the audio is already playing
      if (this.isPlaying) {
        // Stop the currently playing audio
        this.audio.pause();
        this.audio.currentTime = 0;
        this.isPlaying = false;
      }

      // Play the click sound
      this.clickSound.currentTime = 0;
      this.clickSound.play();

      // Delay before playing the animal sound
      setTimeout(() => {
        // Check if the click was not a double-click
        if (!this.isPlaying) {
          // Create a new Audio object and play the animal sound
          this.audio = new Audio(animal.sound);
          this.audio.play();
          this.isPlaying = true;
        }
      }, 300); // Adjust the delay as needed
    },
  },
};
</script>

<style>
body {
  background: linear-gradient(120deg, #fb6f92 15%, #90e0ef 60%);
  color: #f8f9fa;
}
.cardShadow {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;

  background-color: white;
}

img {
  width: 110px;
  height: 110px;
  cursor: pointer;
}

.cardShadow:hover {
  transform: scale(1.5);
}

h3 {
  font-size: 2.3rem;
  color: rgba(6, 6, 127, 0.5);
}
</style>
