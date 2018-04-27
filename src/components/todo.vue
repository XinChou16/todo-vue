<template>
   <div class="todo">
     <p>
       <span>{{todo.text}}</span>
       <button @click=delTodo(index)>删除</button>
     </p>
   </div>
</template>

<script>
export default {
  data: function() {
    return {
      checked3:true,
      lists:[1,2,3]
    }
  },
  props: ['todo','index'],
  methods: {
    delTodo(index) {
      this.$emit('delete',this.index)
    }
  }
}  
</script>

<style>
.fl {
  float: left;
}
</style>

