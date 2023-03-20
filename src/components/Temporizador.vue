<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTempo :tempoEmSegundos="tempoEmSegundos"/>
    <BotaoComponente icone="fas fa-play" texto="play" @aoClicar="iniciar"/>
    <BotaoComponente icone="fas fa-stop" texto="stop" @aoClicar="finalizar" :desativado = "!emFuncionamento"/>
  </div>  
</template>

<script lang="ts">
  import {defineComponent} from "vue";
  import CronometroTempo from "./Cronometro.vue";
  import BotaoComponente from "./Botao.vue";

  export default defineComponent({
    name: "TemporizadorTempo",
    emits: ['aoFinalizarTempo'],
    components: {
      CronometroTempo,
      BotaoComponente
    },
    data() {
      return {
        tempoEmSegundos: 0,
        cronometro: 0,
        emFuncionamento: false
      }
    },
    methods: {
      iniciar() {
        this.emFuncionamento = true,
        this.cronometro = setInterval(() => {
          this.tempoEmSegundos += 1 
       }, 1000)
      },

      finalizar() {
        this.emFuncionamento = false,
        clearInterval(this.cronometro),
        this.$emit('aoFinalizarTempo', this.tempoEmSegundos)
        this.tempoEmSegundos = 0
      }
    }
  })
</script>
