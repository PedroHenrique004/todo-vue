<script setup>
  const props = defineProps(['tarefas','tarefasPendentes', 'statusFiltro'])
</script>

<template>
    <ul v-if="props.statusFiltro == 0">
      <li>
        <h5 class="mt-3">Você não possui tarefas pendentes</h5>
      </li>
    </ul>
   <ul class="list-grou mt-4" v-else>
      <li class="list-group-item" v-for="tarefa in props.tarefas">
        <input :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox" @change="evento => tarefa.finalizada = evento.target.checked">
        <label :class="{done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }

  li {
    list-style-type: none;
  }

</style>
