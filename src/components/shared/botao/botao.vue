<template>
  <button @click="disparaAcao()" class="botao" :class="estiloDoBotao" :type="tipo">{{ rotulo }}</button>
</template>

<script>
  export default {
    props: ['tipo','rotulo','confirmacao', 'estilo'],

    methods:{
      disparaAcao(){
        if (this.confirmacao){
          if (confirm(`Deseja remover esse elemento?`)){
            this.$emit('botaoAtivado');        
          }
          return;
        }
        this.$emit('botaoAtivado');               
      }
    },

    computed: {
       estiloDoBotao() {
           console.log('a', this.estilo);
           // se o valor é padrão ou não passou nada para estilo
           if(this.estilo == 'padrao' || !this.estilo) return 'botao-padrao';
           if(this.estilo == 'perigo') return 'botao-perigo'  ;
       }
   }
  }
</script>

<style scoped>
  .botao {
    display: inline-block;
    padding: 10px;
    border-radius: 3px;
    margin: 10px;
    font-size: 1.2em;
  }

  .botao-perigo {
    background: firebrick;
    color: white;
  }

  .botao-padrao {
    background: darkcyan;
    color: white;
  }
</style>