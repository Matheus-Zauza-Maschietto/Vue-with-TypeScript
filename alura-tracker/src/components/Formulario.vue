<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar ?" v-model="descricao">
            </div>
            <div class="column">
                <TemporizadorItem @ao-temporizador-finalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import {defineComponent} from 'vue'
    import TemporizadorItem from "./Temporizador.vue"

    export default defineComponent({
        name: "Formulario-item",
        components: {
            TemporizadorItem
        },
        data(){
            return {
                descricao: ''
            }
        },
        methods: {
            finalizarTarefa(tempoDecorrido: number): void{
                this.$emit("aoSalvarTarefa", {
                    duracaoEmSegundos: tempoDecorrido,
                    descricao: this.descricao
                })
                this.descricao = ""
            }
        },
        emits: ["aoSalvarTarefa"]
    })
</script>

<style>
    .formulario{
        color: var(--texto-primario);
        background-color: var(--bg-primario);
    }
</style>