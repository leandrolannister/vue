<template>
  <div>
    <h1 class="centralizado">{{ title }}</h1>
    <h2 class="centralizado" v-text="subTitle"></h2>

    <input type="text" class="filtro" @input="filtro = $event.target.value" placeholder="Filtrar titulo">
    {{filtro}}
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="photo in filterInPhotos">
        <meu-painel :titulo="photo.titulo">     
          <imagem-responsiva :url="photo.url" :titulo="photo.titulo"></imagem-responsiva>            
          <meu-botao tipo="button" rotulo="REMOVER"/>
        </meu-painel>  
      </li>
    </ul>
  </div>  
</template>

<script>
  import Painel from '../shared/painel/Painel.vue';
  import ImagemResponsiva from '../shared/img-responsiva/imgResponsiva.vue';
  import Botao from '../shared/botao/botao.vue';
  export default {
    
    components:{
      'meu-painel': Painel,
      'imagem-responsiva':ImagemResponsiva,
      'meu-botao': Botao,
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
