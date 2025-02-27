<!-- where the javascript falls under -->
<script setup>
import {ref} from 'vue';
  
    const newTask = ref('');
    const tasks  = ref(['Task one','Task two', 'Task three',  'Task four']);
    const addTasks = () => {

      if(newTask.value.trim() !== ''){
         tasks.value.push(newTask.value);
         newTask.value = '';
      }
    }
</script>

<template>
  <h3>Tasks:</h3>
    <form @submit.prevent="addTasks">
      <label for="">Add Task: </label>
      <input type="text" id="taskname" name="newtask" v-model="newTask ">
      <button>Add Task</button>
    </form>
  <ul>
    <li v-for="task in tasks" :key="tasks">{{ task }}</li>
  </ul>
</template>


<style scoped>

</style>
