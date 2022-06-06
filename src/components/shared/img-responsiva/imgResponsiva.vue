<template>
  <img class="imagem-responsiva" :src="url" v-bind:alt="titulo">
</template>

<script scoped>
export default{
    props:['url', 'titulo']
}
</script>

<style>
  .imagem-responsiva {
    width: 100%;
  } 
</style>