<!-- where the javascript falls under -->
<script setup>
import {ref} from 'vue';
  
    const name =ref('jane Doe');
    const status = ref('active');
    const tasks  =ref(['task one','task two', 'task three',  'task four']);
    const toogleFunction = () => {
      if(status.value === 'active'){
          status.value = 'pending';
        }
        else if(status.value === 'pending'){
          status.value = 'active'
        }
        else {
          status.value = 'active';
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
