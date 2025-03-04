<!-- where the javascript falls under -->
<script>
   export default{
    data(){
       return {
        name:    'George Kamau',
        status:  "pending",
        tasks:   ['task one','task two','task three','task four','task five'],
        link : 'https://timazi.org'
       }
    },
     methods:{

      toogleFunction(){
        if(this.status === 'active'){
          this.status = 'pending';
        }
        else if(this.status === 'pending'){
          this.status = 'active'
        }
        else {
          this.status = 'active';
        }
      }
     }
  };
  
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status ==='pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{task}}</li>
    <a v-bind:href="link">Click for Google</a> <br>

    <button @click="toogleFunction">Change status</button>
  </ul>
</template>

<!-- Where the styling falls under -->
<style scoped>

</style>







<!-- where the javascript falls under -->
<script setup>
import {onMounted, ref} from 'vue';

  const newtask = ref('');
  const tasks   = ref([]);
  const addTasks= () => {

    if(newtask.value.trim() !== ''){
       tasks.value.push(newtask.value);
       newtask.value = '';
    }
  }
   const deleteTask = (index) => {
    tasks.value.splice(index,1);
   }

   onMounted(async() => {
    try {

      // const response = await fetch('https://jsonplaceholder.typicode.com/todos');
      // const data     = await response.json();
      // tasks.value    = data.map((task) => task.title);
       
    } catch (error) {
      console.log('Error Fetching tasks');
    }
   });
</script>

<template>

  <h3>To do list:</h3> <br><br>
  <!-- The form with action click and input -->
    <form @submit.prevent="addTasks">
      <label for="">To Do List: </label>
      <input type="text" id="input" name="" v-model= "newtask">
       <button id="blue">Add Task</button>
    </form>
      
  <ul>
    <li v-for="(task, index) in tasks" :key="tasks">
     <span> {{ task }}</span>
    <button @click="deleteTask(index)" id="delete">X</button>
    </li>
  </ul>
</template>


<style scoped>
 #delete{
  color: red;
 }
 #blue{
  background-color: lawngreen;
  color:black;
 }
</style>
  
