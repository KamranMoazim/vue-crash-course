// HTML template
<template>
  <div class="container">
    <!-- <h1>Hello Vue</h1> -->
    <Header @toggle-add-task="toggleAddTask" :showAddTask="showAddTask" title="Task Tracker" />
    <!-- <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div> -->
    <!-- <Tasks @toggle-remiander="toggleTemiander" @delete-task="deleteTask" :tasks="tasks" /> -->
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>


// SCRIPTS
<script>
import Header from "./components/Header.vue"
// import Tasks from "./components/Tasks.vue"
// import AddTask from "./components/AddTask.vue"
import Footer from "./components/Footer.vue"

export default {
  name: 'App',
  components: {
    Header,
    // Tasks,
    // AddTask,
    Footer
  },
  data(){
    return {
      // tasks:[],
      showAddTask: false
    }
  },
  methods: {
    // async deleteTask(id){
    //   if (confirm("Are you sure ???")) {
    //     this.tasks = this.tasks.filter((task)=> task.id !== id)
    //     // const res = await fetch(`api/tasks/${id}`,{
    //     //   method:"DELETE"
    //     // })
    //     // // console.log(res)
    //     // res.status === 200 ? (this.tasks = this.tasks.filter((task)=> task.id !== id)) : alert("Error")
    //   }
    // },
    // async toggleTemiander(id){
    //   this.tasks = this.tasks.map((task)=> task.id === id ? {...task, remiander: !task.remiander} : task)
    //   // let taskToToggle = await fetch(`api/tasks/${id}`)
    //   // let taskToToggle = await taskToToggle.json()
    //   // const updTask = {...taskToToggle, remiander: !taskToToggle.remiander}
    //   // console.log(taskToToggle)
    //   // const res = await fetch("api/tasks",{
    //   //   method:"PUT",
    //   //   headers:{ 
    //   //     'Content-type':"application/json",
    //   //   },
    //   //   body:JSON.stringify(updTask)
    //   // })
    //   // // const data = await res.json()
    //   // console.log(res)
    //   // res.status === 200 ? (this.tasks = this.tasks.map((task)=> task.id === id ? {...task, remiander: !task.remiander} : task)) : alert("Error")
    // },
    // async addTask(newTask){
    //   // const res = await fetch("api/tasks",{
    //   //   method:"POST",
    //   //   headers:{ 
    //   //     'Content-type':"application/json",
    //   //   },
    //   //   body:JSON.stringify(newTask)
    //   // })
    //   // const data = await res.json()
    //   this.tasks = [...this.tasks, newTask]
    // },
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    // async fetchTasks(){
    //   const res = await fetch("api/tasks")
    //   const data = await  res.json()
    //   return data;
    // },
    // async fetchTask(id){
    //   const res = await fetch(`api/tasks/${id}`)
    //   const data = await res.json()
    //   return data;
    // },
  },
  // async created(){
  //   this.tasks = [
  //     {
  //       id:1,
  //       text: "Home Appointement",
  //       day: "March 1st at 2:30pm",
  //       remiander: true
  //     },
  //   ]
  //   // this.tasks = await this.fetchTasks()
  // }
}
</script>


// STYLES
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
