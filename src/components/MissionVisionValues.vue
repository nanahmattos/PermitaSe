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
  <div class="Container">
    <div class="carousel">
      <!-- Previous item -->
      <div class="RoundText prev" v-if="items[getPrevIndex()]">
        <h3>{{ items[getPrevIndex()].title }}</h3>
        <p>{{ items[getPrevIndex()].content }}</p>
      </div>

      <!-- Current item -->
      <div class="RoundText selected">
        <h3>{{ items[currentIndex].title }}</h3>
        <p>{{ items[currentIndex].content }}</p>
      </div>

      <!-- Next item -->
      <div class="RoundText next" v-if="items[getNextIndex()]">
        <h3>{{ items[getNextIndex()].title }}</h3>
        <p>{{ items[getNextIndex()].content }}</p>
      </div>

      <div class="buttons">
        <button @click="prev">Anterior</button>
        <button @click="next">Próximo</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.Container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 20px;
  position: relative;
  overflow: hidden;
  width: 100%;
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 100%;
}

.RoundText {
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
  transition:
    transform 0.5s ease,
    opacity 0.5s ease;
}

h3 {
  margin: 0;
}

p {
  margin: 10px 0 0 0;
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
  gap: 10px;
  margin-top: 280px; /* Position below carousel */
}

button {
  padding: 10px;
  background-color: #333;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #555;
}
</style>
