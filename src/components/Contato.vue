<template>
  <section class="contato-container">
    <div>
      <button class="button-whatsApp">Vamos conversar ?</button>
    </div>
    <div>
      <ul class="social">
        <li>
          <a href="#"><img src="../assets/icons/instagram.svg" alt="instagram" /></a>
        </li>
        <li>
          <a href="#"><img src="../assets/icons/facebook.svg" alt="facebook" /></a>
        </li>
      </ul>
    </div>
  </section>
</template>
<style scoped>
.contato-container {
  margin-bottom: 80px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  text-align: center;
}

.button-whatsApp {
  padding: 10px;
  border-radius: 15px;
  margin: 20px;
}
.social {
  display: flex; 
  justify-content: center; 
  align-items: center; 
  gap: 10px; 
  list-style: none; 
}

.social img {
  width: 30px;
  height: 30px;
}
</style>
