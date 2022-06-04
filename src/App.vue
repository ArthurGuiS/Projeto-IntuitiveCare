<template>
  <div class="logotipo">
    <img src="./assets/logo_ic.svg" alt="Logo da Intuitive Care">
  </div>
  <Tabela/>
</template>

<script>
import Tabela from './components/Tabela.vue'

export default {
  name: 'App',
  components: {
    Tabela
  }
}
</script>

<style>
  body{
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
  .logotipo {
    display: flex;
    justify-content: center;
    padding: 9px 0 9px 0;
  }
</style>
