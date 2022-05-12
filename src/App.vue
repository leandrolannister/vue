<template>
  <div>
    <h1>{{ title }}</h1>
    <h2 v-text="subTitle"></h2>
    <ul v-for="photo in photos">
      <li><img :src="photo.url" v-bind:alt="photo.alt"></li>
    </ul>
  </div>  
</template>

<script>
export default {
  data(){
    return{
      title:"Fotos",
      subTitle:"Da Internet",
      photos:[]
    }
  },
  created(){
    let req = this.$http.get('http://localhost:3000/v1/fotos');
    req
    .then(res => res.json())
    .then(data => this.photos = data, error => console.log(`error:${error}`));  
  }    
}
</script>

<style>

</style>
