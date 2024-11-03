<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="headerStyle">
      <nav>
        <ul>
          <li>
            <img src="../src/assets/icons/info.svg" alt="about" />
            <RouterLink to="/">Sobre</RouterLink>
          </li>
          <li>
            <img src="../src/assets/icons/list.svg" alt="services" />
            <RouterLink to="/servicos">Serviços</RouterLink>
          </li>
          <li>
            <img src="../src/assets/icons/fit.svg" alt="workout" />
            <RouterLink to="/treino">Treino</RouterLink>
          </li>
          <li>
            <img src="../src/assets/icons/chat.svg" alt="contact" />
            <RouterLink to="/contato">Contato</RouterLink>
          </li>
        </ul>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.headerStyle {
  position: fixed;
  z-index: 1;
  bottom: 0;
  background-color: #9c9c9c;
  padding: 15px;
  width: 100vw;

  ul {
    display: flex;
    align-items: end;
    justify-content: space-between;
    li {
      display: flex;
      text-align: center;
      flex-direction: column;
      img {
        width: 50px;
      }
    }
  }
}
</style>
