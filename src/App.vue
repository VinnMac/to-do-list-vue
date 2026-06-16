<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

  const estado = reactive({
    tarefaTemp: '',

    filtro: 'todas',

    tarefas: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar Angular',
        finalizada: true,
      },
      {
        titulo: 'Ir à academia',
        finalizada: false,
      }
    ]
  })

  const getTarefasPendentes = () => estado.tarefas.filter (tarefa => !tarefa.finalizada)

  const getTarefasFinalizadas = () => estado.tarefas.filter (tarefa => tarefa.finalizada)

  const getTarefasFiltradas = () => {
    const { filtro } = estado;

    switch (filtro) {
      case 'pendentes':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas();
      default:
        return estado.tarefas;
    }
  }



  const getNumeroTarefasPendentes = () => getTarefasPendentes().length;

  const frasePlural = () => getNumeroTarefasPendentes() > 1 
    ? 'tarefas pendentes' 
    : 'tarefa pendente';

  const cadastraTarefa = () => {
    const novaTarefa = {
      titulo: estado.tarefaTemp,
      finalizada: false
    }
    estado.tarefas.push(novaTarefa);
    estado.tarefaTemp = '';
  } 

</script>

<template>
  <div class="container">
    <Cabecalho :numero-tarefas-pendentes="getNumeroTarefasPendentes()" :frase-plural="frasePlural()" />
    <Formulario :cadastra-tarefa="cadastraTarefa" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :troca-filtro="evento => estado.filtro = evento.target.value"  />
    <ListaDeTarefas :tarefas="getTarefasFiltradas()" />
    
    
  </div>
</template>
