<template>
  <button class="button" @click="clique" :disabled=desativado>
    <span class="icon">
        <i :class=icone></i>
    </span>
    <span>{{texto}}</span>
  </button>
</template>

<script lang="ts">
  
  import {defineComponent} from "vue";

  export default defineComponent({
    name: "BotaoComponente",    
    emits: ['aoClicar'],
    props: {
      icone: String,
      texto: String,
      desativado: Boolean
    },
    methods: {
      clique() {
        this.$emit('aoClicar')
      }
    }
  })

</script>
