<template>
  <div :key="task.id" v-for="task in tasks">
        <!-- <h3>{{task.text}}</h3> -->
        <Task 
            @toggle-remiander="$emit('toggle-remiander', task.id)" 
            @delete-task="$emit('delete-task', task.id)" 
            :task="task" 
        />
  </div>
</template>

<script>
import Task from "./Task.vue"

export default {
    name:"Tasks",
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    emits: ['delete-task', 'toggle-remiander']
}
</script>

<style scope>

</style>