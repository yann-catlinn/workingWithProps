<template>
  <div id="app">
    <a href="#" @click="deleted(id)">
        <input class="delete" value="delete">
    </a>
  </div>
</template>

<script>
  export default {
    name: "event_delete",
    props:{
      id:{
          type:Number,
          required:true,
      },
    },
    data() {
      return {
        message: "",
        
      };
    },
    methods:{
        deleted(id){
        this.$emit("deleted",{id:id})
        },
    },
    mounted:function(){
       // this.count()
    }
  }

</script>

<style scoped>
</style>
