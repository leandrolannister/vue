<template>
  <div class="corpo">
    <h1 class="centralizado">{{ title }}</h1>
    <h2 class="centralizado" v-text="subTitle"></h2>
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="photo in photos">        
        <div class="painel">
          <h2 class="painel-titulo">{{photo.titulo}}</h2>
          <div class="painel-corpo">
            <img class="imagem-responsiva" :src="photo.url" v-bind:alt="photo.alt">
          </div>
        </div>
      </li>
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

   .lista-fotos .lista-fotos-item {
    display: inline-block;
  }

  .imagem-responsiva {
    width: 100%;
  }

  .painel {
    padding: 0 auto;
    border: solid 2px grey;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    border: solid 2px;
    background: lightblue;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
  }
</style>
