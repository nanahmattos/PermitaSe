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


// Variáveis para o gesto
let startX = 0
let currentTranslate = 0
let prevTranslate = 0
let isDragging = false

// Handlers de evento
const onTouchStart = (event) => {
  startX = event.touches[0].clientX
  isDragging = true
}

const onTouchMove = (event) => {
  if (!isDragging) return
  const currentX = event.touches[0].clientX
  currentTranslate = prevTranslate + currentX - startX
}

const onTouchEnd = () => {
  isDragging = false

  // Lógica de navegação
  if (currentTranslate - prevTranslate > 50) {
    prev()
  } else if (currentTranslate - prevTranslate < -50) {
    next()
  }

  // Reseta o translate
  currentTranslate = 0
  prevTranslate = 0
}
</script>

<template>
  <section class="carousel-container">
    <div class="carousel" @touchstart="onTouchStart"
      @touchmove="onTouchMove"
      @touchend="onTouchEnd">
      <div class="carousel-text prev" v-if="items[getPrevIndex()]">
        <h3>{{ items[getPrevIndex()].title }}</h3>
        <p>{{ items[getPrevIndex()].content }}</p>
      </div>

      <div class="carousel-text selected">
        <h3>{{ items[currentIndex].title }}</h3>
        <p>{{ items[currentIndex].content }}</p>
      </div>

      <div class="carousel-text next" v-if="items[getNextIndex()]">
        <h3>{{ items[getNextIndex()].title }}</h3>
        <p>{{ items[getNextIndex()].content }}</p>
      </div>
    </div>

    <div class="buttons-carousel">
      <button @click="prev">
        <img src="../assets/icons/left.svg" alt="left" />
      </button>
      <button @click="next">
        <img src="../assets/icons/rigth.svg" alt="right" />
      </button>
    </div>

    <div class="background-image">
      <div class="overlay-text">
        <h1>Thayanni Rosa</h1>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Corrupti atque ad maxime autem
          corporis enim voluptates consequuntur inventore soluta, nesciunt nisi est quia quis
          minima, suscipit a quam neque quo!
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.carousel-container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
}

.carousel {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.carousel-text {
  background-color: #9b9b9b;
  position: absolute;
  top: 0;
  border-radius: 50%;
  text-align: center;
  width: 250px;
  height: 250px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding: 20px;
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

.buttons-carousel {
  position: absolute;
  z-index: 2;
  top: 30%; 
  width: 100%;
  display: flex;
  justify-content: center;
  transform: translateY(-50%);
}

.buttons-carousel button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.buttons-carousel img {
  width: 20px;
  height: 20px;
}

.background-image {
  position: absolute;
  z-index: -1;
  top: 30%;
  left: 0;
  right: 0;
  background-image: url('../assets/images/IMG_0901.JPEG');
  background-size: cover;
  background-position: center;
  height: 70vh;
}

.overlay-text {
  color: white;
  text-align: center;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0));
  padding: 20px;
  border-radius: 8px;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: end;
  align-items: center;
  flex-direction: column;
}

@media (max-width: 768px) {
}
</style>
