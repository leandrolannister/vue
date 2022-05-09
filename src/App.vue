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
      data:[{
        url:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT3rQF_7DTCAImmw69SlDWKpCABocHMLmwinw&usqp=CAU",
        alt:"Moto"
      }]  
    }
  }
}
</script>

<style>

</style>
