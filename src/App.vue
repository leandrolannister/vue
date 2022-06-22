<template>
  <div class="corpo">
    <nav>
      <li v-for="route in routes">
        <router-link :to="route.path ? route.path : '/'">{{route.titulo}}</router-link>
      </li>
    </nav>

    <transition name="pagina">
      <router-view></router-view>
    </transition>
    
  </div>  
</template>

<script>
  import {routes} from './routes';
  export default {
    data(){
      return {routes:routes}
    }
  }
</script>

<style>
   .corpo {
     font-family: Helvetica, sans-serif;
     width: 96%;
     margin: 0 auto;
   }

   .pagina-enter-active, .pagina-leave-active {
     transition: opacity .3s
   }
   
   .pagina-enter, .pagina-leave-active {
     opacity: 0
   }   
</style>
