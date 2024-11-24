<script setup>
import { ref } from 'vue'

const items = ref([
  {
    title: 'Treinamento personalizado',
    content:
      'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo impedit soluta, alias similique voluptatum commodi nostrum.'
  }
])
</script>
<template>
  <section class="servicos-container">
    <h1 class="title">Serviços</h1>
    <div>

    </div>

    <div class="servicos-card">
      <img src="../assets/icons/fit.svg" alt="peso" />
      <div class="servicos-text">
        <h3>
          {{ items[0].title }}
        </h3>
        <p>
          {{ items[0].content }}
        </p>
      </div>
    </div>
    <div class="servicos-card">
      <div class="servicos-text">
        <h3>
          {{ items[0].title }}
        </h3>
        <p>
          {{ items[0].content }}
        </p>
      </div>
      <img src="../assets/icons/fit.svg" alt="peso" />
    </div>
    <div class="servicos-card">
      <img src="../assets/icons/fit.svg" alt="peso" />
      <div class="servicos-text">
        <h3>
          {{ items[0].title }}
        </h3>
        <p>
          {{ items[0].content }}
        </p>
      </div>
    </div>
  </section>
</template>
<style scoped>
.servicos-container {
  width: 100%;
}
.servicos-card {
  display: flex;
  justify-content: space-between;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  gap: 20px;
  align-items: center;
  margin: 5px;
  padding: 10px;
  border-radius: 15px;
  background-color: rgb(93, 94, 93);
}
.servicos-card img {
  width: 50px;
  height: 50px;
}

.servicos-text {
  text-align: start;
}
</style>
