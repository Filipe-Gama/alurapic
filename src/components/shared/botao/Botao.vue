<template>
  <button @click="disparaAcao()" :class="estiloBotao" :type="tipo">{{ rotulo }}</button>
</template>

<script>
export default {
  

  props: {

    tipo: {
      required: true,
      type:String
    },

    rotulo: {
      required: true,
      type:String
    },

    confirmacao: Boolean,
    estilo: String
  },

  methods: {

    disparaAcao() {
      if(this.confirmacao) {
          if(confirm('Confirmar remoção?')){
          this.$emit('botaoAtivado');
        }
        return;
      }
      this.$emit('botaoAtivado');

    }
  },

  computed: {

    estiloBotao() {
      
      if(this.estilo == 'padrao' || !this.estilo) return 'botao botao-padrao';
      if(this.estilo == 'perigo') return 'botao botao-perigo';
    }

  }
}
</script>
  
<style>

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

  .botao-padrao{
    background: darkcyan;
    color: white;
  }
</style>