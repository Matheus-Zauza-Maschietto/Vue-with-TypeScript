
<template>
    <BoxItem>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || "Tarefa sem descrição"}}
            </div>
            <div class="column">
                <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxItem>
</template>

<script lang="ts">
import { PropType } from 'vue'
import Cronometro from './Cronometro.vue'
import ITarefa from '../interfaces/ITarefa'
import BoxItem from "./box.vue"
export default ({
    name: "TarefaItem",
    components: { Cronometro, BoxItem },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

<style scoped>
    .box{
        background: #Fafcaf;
    }
</style>