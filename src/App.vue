<template>
  <div>
    <h1>{{ title }}</h1>
    <h2 v-text="subTitle"></h2>
    <ul v-for="p in data">
      <li><img :src="p.url" v-bind:alt="p.alt"></li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      title:"Tiger 660",
      subTitle:"Triump",
      data:[]  
    }
  },
  created(){
    alert("Welcome to Life Hook")
  }
}
</script>

<style>

</style>
