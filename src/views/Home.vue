<template>
<div>
    <div v-show="showAddTask">
        <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-remiander="toggleTemiander" @delete-task="deleteTask" :tasks="tasks" />
</div>
</template>

<script>

import Tasks from "../components/Tasks.vue"
import AddTask from "../components/AddTask.vue"

export default {
  name: 'Home',
  components: {
    Tasks,
    AddTask
  },
  props:{
      showAddTask:Boolean
  },
  data(){
    return {
      tasks:[],
    //   showAddTask: false
    }
  },
  methods: {
    async deleteTask(id){
      if (confirm("Are you sure ???")) {
        this.tasks = this.tasks.filter((task)=> task.id !== id)
      }
    },
    async toggleTemiander(id){
      this.tasks = this.tasks.map((task)=> task.id === id ? {...task, remiander: !task.remiander} : task)
    },
    async addTask(newTask){
      this.tasks = [...this.tasks, newTask]
    },
    // toggleAddTask(){
    //   this.showAddTask = !this.showAddTask
    // },
    async fetchTasks(){
      const res = await fetch("api/tasks")
      const data = await  res.json()
      return data;
    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`)
      const data = await res.json()
      return data;
    },
  },
  async created(){
    this.tasks = [
      {
        id:1,
        text: "Home Appointement",
        day: "March 1st at 2:30pm",
        remiander: true
      },
    ]
  }
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>