<script setup>
    const props = defineProps(['tarefas']);
</script>
<template>
   <div>
    <!-- Exibe a lista de tarefas se houver mais de zero itens -->
    <ul class="list-group mt-4" v-if="props.tarefas.length > 0">
        <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.id">
            <input 
                @change="evento => tarefa.finalizada = evento.target.checked" 
                :checked="tarefa.finalizada" 
                :id="tarefa.titulo" 
                type="checkbox"
            >
            <label :class="{done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    
    <!-- Mensagem alternativa quando não há tarefas -->
    <p v-else class="mt-4">Não existem tarefas pendentes</p>
</div>


</template>

<style scoped>
    .done{
    text-decoration: line-through;
    }
</style>