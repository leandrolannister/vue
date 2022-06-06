<template>
  <div class="corpo">
    <h1 class="centralizado">{{ title }}</h1>
    <h2 class="centralizado" v-text="subTitle"></h2>

    <input type="text" class="filtro" @input="filtro = $event.target.value" placeholder="Filtrar titulo">
    {{filtro}}
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="photo in filterInPhotos">
        <meu-painel :titulo="photo.titulo">     
          <imagem-responsiva :url="photo.url" :titulo="photo.titulo"></imagem-responsiva>            
        </meu-painel>  
      </li>
    </ul>
  </div>  
</template>

<script>
  import Painel from './components/shared/painel/Painel.vue';
  import ImagemResponsiva from './components/shared/img-responsiva/imgResponsiva.vue';
  export default {
    
    components:{
      'meu-painel': Painel,
      'imagem-responsiva':ImagemResponsiva
    },

    data(){
      return{
        title:"Fotos",
        subTitle:"Da Internet",
        photos:[],
        filtro:''
      }
    },
    computed:{
       filterInPhotos(){
         if (this.filtro){
           let exp = new RegExp(this.filtro.trim(), 'i');
           return this.photos.filter(photo => exp.test(photo.titulo));
         }else{
           return this.photos;
         }  
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

   .filtro {
     display: block;
     width: 100%;
   }

   .lista-fotos {
     list-style: none;
   }

   .lista-fotos .lista-fotos-item {
    display: inline-block;
  }
</style>
