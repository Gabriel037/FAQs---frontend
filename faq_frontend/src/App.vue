<template>
  <div class="app-view">
    <System/>
  </div>
</template>

<script>
import System from './components/System.vue'

export default {
  name: 'App',
  components: {
    System
  }
}
</script>

<style>
body, html {
	margin: 0;
	padding: 0;
	font-family: 'poppins', sans-serif;
  overflow-x: hidden;
}
.app-view {
  overflow: hidden;
  padding: 0;
  margin: 0;
	min-height: 100vh;
	min-width: 100vw;
  height: 100%;
  width: 100%;
}

:root {
  --azul: #000013;
  --branco: #fefefe;
  --roxo_claro: #6F6C90;
  --roxo_fundo: #F7F7FB1A;
  --azul_claro: #3f34b9;
}
</style>
