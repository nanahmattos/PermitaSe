<script setup>
import Hero from '@/components/Hero.vue'
import MissionVisionValues from '@/components/MissionVisionValues.vue'
import Servicos from '@/components/Servicos.vue'
import Depoimentos from '@/components/Depoimentos.vue';
import Metodos from '@/components/Metodos.vue';
import Contato from '@/components/Contato.vue';
</script>
<template>
  <main>
    <div>
      <Hero id="about" />
      <MissionVisionValues  />
      <Servicos id="services" />
      <Metodos id="treino" />
      <Depoimentos />
      <Contato id="contato"  />
    </div>
  </main>
</template>
<style scoped>
</style>