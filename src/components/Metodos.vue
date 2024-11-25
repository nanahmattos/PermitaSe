<script setup></script>
<template>
  <section>
    <h1 class="title">Método de treinamento</h1>
    <div class="metodo-container">
      <div class="metodo-card">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat, voluptas vero. Rerum
          expedita obcaecati exercitationem facilis? Molestias quae dolor maiores vitae iste.
          Molestias non dignissimos unde error expedita optio explicabo.
        </p>
      </div>
    </div>
  </section>
</template>
<style scoped>
.metodo-container {
  justify-content: center;
  align-items: center;
  display: flex;
  flex-direction: column;
  background-image: url('../assets/images/rockslove.svg');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: right;
}
.metodo-card {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(3px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.4);
  box-shadow:
    0 4px 6px rgba(0, 0, 0, 0.1),
    0 0 10px rgba(255, 255, 255, 0.5) inset;
  width: 300px;
  text-align: center;
  padding: 15px;
  margin: 10px;
}
</style>
