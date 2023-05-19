<template>
  <div>
    <!-- <ul>
      <li v-for="animal in animalLand" :key="animal.id">
        {{ animal.name }}
        <img :src="animal.imageSrc" alt="pix" />
      </li>
    </ul> -->
  </div>
  <div class="container px-5">
    <div class="row gap-5">
      <div
        class="col justify-content-center align-items-center cardShadow"
        v-for="animal in animalLand"
        :key="animal.id"
      >
        <img :src="animal.imageSrc" alt="loading..." />
      </div>
    </div>
  </div>
</template>
<script>
import { animalLand } from "../assets/gameData";
export default {
  data() {
    return {
      animalLand: animalLand,
    };
  },
};
</script>
<style>
.cardShadow {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}
img {
  width: 100px;
  height: 90px;
  cursor: pointer;
}
.cardShadow:hover {
  transform: scale(1.5);
}
</style>
