<script setup>
import { reactive, ref } from "vue";
import AddTask from "./components/AddTask.vue";

const tasks = ref([]);

const task = reactive({
  tarea: "",
  state: false,
});

const doneTasks = tasks.value.filter((task) => {
  return task.state === true;
}).length;

const totalTasks = tasks.value.length;

const addNewTask = (text) => {
  tasks.value.push({
    tarea: text,
    state: false,
  });

  Object.assign(task, {
    tarea: "",
    state: false,
  });
};
</script>

<template>
  <main class="container">
    <h1>Lista de Tareas</h1>
    <h2>Se han completado {{ doneTasks }} de {{ totalTasks }}</h2>
    <AddTask v-model:tarea="task.tarea" @add-new-task="addNewTask" />
  </main>
</template>

