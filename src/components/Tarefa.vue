<template>
  <BoxCard>
    <div class="columns">
      <div class="column is-7">
        {{tarefa.descricao || 'Tarefa sem descrição'}}
      </div>
      <div class="column">
        <CronometroTempo :tempoEmSegundos = "tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </BoxCard>

</template>

<script lang="ts">
  import {defineComponent, PropType} from 'vue';
  import CronometroTempo from './Cronometro.vue';
  import ITarefa from '../interfaces/ITarefa';
  import BoxCard from './Box.vue';

  export default defineComponent({
    name: "TarefaTempo",
    components: {
      CronometroTempo,
      BoxCard,
    },
    props: {
      tarefa: {
        type: Object as PropType<ITarefa>, 
        required: true
      }
    }
  })
</script>

<style scoped>
  .box {
    background: #FAF0CA;
  }

</style>
