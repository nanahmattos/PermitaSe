<script setup>
import { ref } from 'vue'
import imageEu from '../assets/images/eu.jpeg'

const items = ref([
  {
    title: 'Amanda Silva',
    age: 32,
    content:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo impedit soluta, alias similique voluptatum commodi nostrum.',
    image: imageEu
  },
  {
    title: 'Gabriela Pereira',
    age: 25,
    content:
      'Aliquid officia debitis excepturi atque natus animi quidem voluptatem labore beatae ad quia.',
    image: imageEu
  },
  {
    title: 'Maria Souza',
    age: 65,
    content:
      'Facilis porro quos quia consequatur maxime architecto. Cupiditate autem eaque enim distinctio quam soluta.',
    image: imageEu
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
  <section class="depoimentos-container">
    <h1 class="title">Depoimentos</h1>

    <div class="depoimentos">
      <div class="depoimentos-text prev" v-if="items[getPrevIndex()]">
        <div class="depoimentos-image">
          <img :src="items[getPrevIndex()].image" alt="treinamento" />
        </div>
        <h3>{{ items[getPrevIndex()].title }}</h3>
        <h4>{{ items[getPrevIndex()].age }} anos</h4>
        <p>{{ items[getPrevIndex()].content }}</p>
      </div>

      <div class="depoimentos-text selected">
        <div class="depoimentos-image">
          <img :src="items[currentIndex].image" alt="treinamento" />
        </div>

        <h3>{{ items[currentIndex].title }}</h3>
        <h4>{{ items[currentIndex].age }} anos</h4>
        <p>{{ items[currentIndex].content }}</p>
      </div>

      <div class="depoimentos-text next" v-if="items[getNextIndex()]">
        <div class="depoimentos-image">
          <img :src="items[getNextIndex()].image" alt="treinamento" />
        </div>
        <h3>{{ items[getNextIndex()].title }}</h3>
        <h4>{{ items[getNextIndex()].age }} anos</h4>
        <p>{{ items[getNextIndex()].content }}</p>
      </div>
    </div>

    <div class="buttons-depoimentos">
      <button @click="prev">
        <img src="../assets/icons/left.svg" alt="left" />
      </button>
      <button @click="next">
        <img src="../assets/icons/rigth.svg" alt="right" />
      </button>
    </div>
  </section>
</template>
<style scoped>
.depoimentos-container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 50vh;
  overflow: hidden;
}

.depoimentos {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.depoimentos-text {
  background-color: #555252;
  border-radius: 15px;
  position: absolute;
  top: 0;
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

.depoimentos-image {
  overflow: hidden;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.depoimentos-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
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

/* invisible buttons */
.buttons-depoimentos {
  position: absolute;
  z-index: 2;
  top: 50%;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
}

.buttons-depoimentos button {
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.buttons-depoimentos img {
  width: 40px;
  height: 40px;
}
</style>
