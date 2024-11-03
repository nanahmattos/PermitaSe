<script setup>
import { ref } from 'vue'

const items = ref([
  {
    title: 'Missão',
    content:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo impedit soluta, alias similique voluptatum commodi nostrum.'
  },
  {
    title: 'Visão',
    content:
      'Aliquid officia debitis excepturi atque natus animi quidem voluptatem labore beatae ad quia.'
  },
  {
    title: 'Valores',
    content:
      'Facilis porro quos quia consequatur maxime architecto. Cupiditate autem eaque enim distinctio quam soluta.'
  }
])

const currentIndex = ref(0)

const next = () => {
  currentIndex.value = (currentIndex.value + 1) % items.value.length
}

const prev = () => {
  currentIndex.value = (currentIndex.value - 1 + items.value.length) % items.value.length
}

const getPrevIndex = () => (currentIndex.value - 1 + items.value.length) % items.value.length
const getNextIndex = () => (currentIndex.value + 1) % items.value.length
</script>

<template>
  <section class="Container">
    <div class="carousel">
      <!-- Previous item -->
      <div class="roundText prev" v-if="items[getPrevIndex()]">
        <h3>{{ items[getPrevIndex()].title }}</h3>
        <p>{{ items[getPrevIndex()].content }}</p>
      </div>

      <!-- Current item -->
      <div class="roundText selected">
        <h3>{{ items[currentIndex].title }}</h3>
        <p>{{ items[currentIndex].content }}</p>
      </div>

      <!-- Next item -->
      <div class="roundText next" v-if="items[getNextIndex()]">
        <h3>{{ items[getNextIndex()].title }}</h3>
        <p>{{ items[getNextIndex()].content }}</p>
      </div>

      <div class="buttons">
        <button @click="prev">
          <img src="../assets/icons/left.svg" alt="left" />
        </button>
        <button @click="next">
          <img src="../assets/icons/rigth.svg" alt="right" />
        </button>
      </div>
    </div>
    <div class="background-image">
      <div class="overlay-text">
        <h1>Thayanni Rosa</h1>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Corrupti atque ad maxime autem
          corporis enim voluptates consequuntur inventore soluta, nesciunt nisi est quia quis minima,
          suscipit a quam neque quo!
        </p>
      </div>
    </div>
  </section>
  
</template>

<style scoped>
.Container { 
  width: 100vw;  
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  z-index: 1;
  width: 100vw;
  height: 50vh;
}

.roundText {
  background-color: green;
  border-radius: 50%;
  text-align: center;
  width: 250px;
  height: 250px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  position: absolute;
  z-index: 1;
  transition:
    transform 0.5s ease,
    opacity 0.5s ease;
}


.selected {
  z-index: 2;
  transform: translateX(0) scale(1);
  opacity: 1;
}

.prev {
  transform: translateX(-150px) scale(0.8);
  opacity: 0.5;
  z-index: 1;
}

.next {
  transform: translateX(150px) scale(0.8);
  opacity: 0.5;
  z-index: 1;
}

.buttons {
  display: flex;
  position: absolute;
  z-index: 1;
  justify-content: space-between;
  width: 100vw;
  
  button {
    background-color: transparent;
    border: none;
  }
}

.background-image {
  position: relative;
  top: 40vh; 
  left: 0;
  right: 0;
  background-image: url('../assets/IMG_0901.JPEG');
  background-size: cover;
  background-position: center;
  height: 70vh;
  
}
.overlay-text {
  color: white;
  text-align: center;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.7),
    rgba(0, 0, 0, 0)
  );
  padding: 20px;
  border-radius: 8px;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: end;
  align-items: center;
  flex-direction: column;
}

</style>
