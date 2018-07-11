<template>
  <div class="container">
    <h3>{{ title }}</h3>
    <form>
    <textarea placeholder="Add new Task" v-model="newTask"></textarea>
    <p>{{newTask}}</p>
    <button type="button" v-on:click="addTask" > Add Task {{tasks.length}} </button>
    </form>

    <ul>
    <li v-for="tasks in tasks"> {{tasks}} 

    </li>
    </ul>
    


   
    

  </div>
  
</template>

<script>
export default {
  data: function() {
    return {
      title: 'My First App',
      click: 0 ,
      newTask:'SAMPLE',
      
      tasks:[
      
      ]
    }
  },
  methods:{
    addTask(){
      this.tasks.unshift(this.newTask);
      this.newTask = '';
    
    }
  }
}
</script>
