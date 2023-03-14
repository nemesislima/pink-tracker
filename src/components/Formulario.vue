<template>
    <!--div.box já cria automaticamente a tag com a class especificada após o ponto-->
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">

                <temporizador @aoTemporizadorFinalizado="finalizarTarefa"></temporizador>
                
            </div>
        </div>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import Temporizador from './Temporizador.vue'

export default defineComponent ({
    name: "Formulário",
    emits: ['aoSalvarTarefa'],
    components: {
        Temporizador
    },
    data () {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa (tempoDecorrido: number) : void {
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            }),
            this.descricao = ''
        }
    }
    // data () {
    //     return {
    //         tempoEmSegundos: 0,
    //         cronometro: 0
    //     }
    // },

    // methods: {

    //     iniciar () {
    //         //1 seg = 1000 ms
    //         this.cronometro = setInterval ( () => {
    //             this.tempoEmSegundos += 1
                
    //         }, 1000)

    //         //console.log("iniciando")
            
    //     },

    //     finalizar () {
    //         //console.log("finalizando")

    //         clearInterval (this.cronometro) 
            
    //     }

    // }
});

</script>

<style>

.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}

</style>
