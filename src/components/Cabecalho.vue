<script setup>
    const props = defineProps(['numeroTarefasPendentes', 'frasePlural']);
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui {{ props.numeroTarefasPendentes }} {{ props.frasePlural }}
        </p>
    </header>
</template>