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
