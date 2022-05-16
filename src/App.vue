<template>
  <div class="corpo">
    <h1 class="centralizado">{{ title }}</h1>
    <h2 class="centralizado" v-text="subTitle"></h2>
    <ul class="lista-fotos" v-for="photo in photos">
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
   .corpo {
     font-family: Helvetica, sans-serif;
     width: 96%;
     margin: 0 auto;
   }

   .centralizado {
     text-align: center;
   }

   .lista-fotos {
     list-style: none;
   }

   .lista-fotos{
     display: inline-block;
   }
</style>
