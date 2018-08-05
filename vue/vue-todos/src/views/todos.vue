<template>
  <div class="todos">
    <h2>todos</h2>
    <input class="new-todo"
    autofocus autocomplete="off"
    placeholder="What needs to be done?"
    v-model="newTodo"
    @keyup.enter="addTodo">
    <div class="main">
        <ul class="todo-list" v-if="todos.length">
        <li v-for="todo in todos" v-bind:key = 'todo.id' >
            <input class="toggle" type="checkbox" v-model="todo.done">
            <span :class="{ done: todo.done}">{{todo.content}}</span>
            <button class="remove" @click="removetodo(todo)">X</button>
        </li>
    </ul>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'Todos',
  data () {
    return {
      todos: [],
      newTodo:''
    }
  },
  methods:{
    addTodo:function(){
        let value = this.newTodo && this.newTodo.trim()
        if(!value){
            return
        }
        this.todos.push({done:false,content:value})
        this.newTodo = ''
    },
    removetodo:function(todo){
        this.todos.splice(this.todos.indexOf(todo),1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='less'>
.todos{
    ul li{
        list-style: none;
        text-align: left;
        line-height: 35px;
    }
    ul{
        padding-left: 0;
    }
    .done{
        color: #666;
        text-decoration:line-through
    }
    .todo-list{
        width: 400px;
    }
    .main{
        width: 400px;
        background-color: aquamarine;
        margin: 0 auto;
        
    }
    .new-todo{
        width: 250px;
        height: 25px;
        font-size: 14px;
        padding-left: 10px;
        border-radius: 4px;
        border: 1px solid #e6e6e6;
    }
}
</style>

