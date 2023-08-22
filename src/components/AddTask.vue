<script setup>
const props = defineProps({
  tarea: {
    type: String,
    required: true,
  },
});
const emit = defineEmits(["update:tarea", "add-new-task"]);
</script>

<template>
  <div class="task-add">
    <input
      type="text"
      placeholder="¿Qué tienes planeado para hoy?"
      id="tarea"
      :value="tarea"
      @input="$emit('update:tarea', $event.target.value)"
    />
    <button @click="$emit('add-new-task', tarea)">Agregar Tarea</button>
  </div>
</template>