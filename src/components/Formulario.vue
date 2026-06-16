<script setup>
    const props = defineProps(['cadastraTarefa', 'tarefaTemp', 'editaTarefaTemp', 'trocaFiltro'  ]);
</script>

<template>
    <form @submit.prevent="props.cadastraTarefa">
        <div class="row">
            <div class="col">
                <input required :value="props.tarefaTemp" @change="props.editaTarefaTemp" class="form-control" type="text" placeholder="Digite a descrição da tarefa">
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar</button>
            </div>
            <div class="col-md-2">
                <select @change="props.trocaFiltro" class="form-control">
                    <option value="todas">Todas as tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizadas">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>