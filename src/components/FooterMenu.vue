<script setup>
function scrollToSection(id) {
  const section = document.getElementById(id)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>
<template>
  <footer class="footerStyle">
    <nav>
      <ul>
        <li>
          <a @click.prevent="scrollToSection('about')">
            <img src="../assets/icons/info.svg" alt="about" />
            <span>Sobre</span>
          </a>
        </li>
        <li>
          <a @click.prevent="scrollToSection('services')">
            <img src="../assets/icons/list.svg" alt="services" />
            <span>Serviços</span>
          </a>
        </li>
        <li>
          <a @click.prevent="scrollToSection('treino')">
            <img src="../assets/icons/fit.svg" alt="workout" />
            <span>Treino</span>
          </a>
        </li>
        <li>
          <a @click.prevent="scrollToSection('contato')">
            <img src="../assets/icons/chat.svg" alt="contact" />
            <span>Contato</span>
          </a>
        </li>
      </ul>
    </nav>
  </footer>
</template>

<style scoped>
.footerStyle {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #fff;
  padding: 10px 0;
  box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.2);
  z-index: 10;
}

nav ul {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 0;
  margin: 0;
  list-style: none;
}

nav ul li a {
  text-decoration: none;
  color: #000;
  font-size: clamp(0.6875rem, 0.5rem + 1vw, 0.875rem);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

nav ul li a img {
  width: 24px;
  margin-bottom: 5px;
}
</style>
