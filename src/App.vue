<template>
  
  <div id="app">
      <h1>Working with Props - To do List</h1>
      <form>
          <label for="">Tasks</label>
          <input type="text" v-model="task" @keyup.enter="add_task" placeholder="Add a new Task">
          <input v-on:click.prevent=add_task type="submit" value="Add">
      </form>
      <ul id="task_div">
          <li v-for="(task, index) in tasks"
          :task="task"
          :index="index"
          :key="task.id"
          >
              {{task}}
              <event-delete :id="index" @deleted="delete_task"></event-delete>
          </li>
      </ul>
  </div>
</template>

<script>
   import DeleteComponent from "./components/Delete.vue";
  export default {
      name: 'app-component',
      // props:{},
    data: function() {
      return {
                 tasks:[],
          task:"",
      };
    },
    // computed:{},
     components: {
          'event-delete':DeleteComponent,
      },
    methods:{
         add_task: function (task, index) { 
            if(this.task != ""){
            this.tasks.push(this.task)
            this.task="";
            }
        },
        delete_task(e){
          console.log(e,"event")
          let id= e.id
          let index=this.tasks.findIndex((task)=>task.id===id);
          console.log(id)
          this.tasks.splice(id,1)
    }
    }  
  }
  
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    text-align: center;
  }
  #task_div{
      display: flex;
      flex-direction: column;
      justify-content: center;
  }
  #task_div li{
        display: flex;
   
      justify-content: center;
  }

 
</style>