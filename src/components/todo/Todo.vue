<template>
  <div id="todoApp">
    <h1>Todo App</h1>
    <input type="text" placeholder="Add new todo item" v-model="todo" v-bind:class="{ active : isActive }" @keyup.enter="addItem">

    <ul v-if="todoList.length > 0">
      <li v-for="(item, index) in todoList" v-bind:key="index">{{item}} <button @click="removeItem(index)">X</button> </li>
    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      todo: "",
      todoList: [],
    };
  },

  computed: {
    isActive(){
      return this.todo.length > 0;
    }
  },

  methods: {
    addItem(){
      this.todoList.push(this.todo);
      this.todo = "";
    },

    removeItem(index){
      this.todoList.splice(index,1);
    }
  }
}
</script>

<style scoped>
  #todoApp{
    max-width: 400px;
    margin: 20px auto;
    border: 1px solid black;
    padding: 15px;
    font-family: Arial, Helvetica, sans-serif;
    background-color: #8601ff;
  }
  h1{
    text-align: center;
    color: #333333;
    text-transform: uppercase;
  }
  input{
    width: 100%;
    box-sizing: border-box;
    padding: 10px;
    border: none;
    outline: none;
    box-shadow: 0px 3px #fbff00;
    background-color: #333333;
    color: #fff;
  }
  input::placeholder{
    color: #fff;
  }
  input.active{
    box-shadow: 0px 3px #00ff43;
  }
  ul{
    list-style: none;
    margin:0px;
    padding:0px;
    margin-top:25px;
  }
  ul li{
    padding: 5px 15px;
    border: 1px solid #333333;
    display:flex;
    font-size: 12px;
    color: #333;
    background-color: #fff;
  }
  ul li + li{
    border-top: none;
  }
  ul li button{
    outline: none;
    border: 1px solid #bdbdbd;
    background-color: transparent;
    margin-left: auto;
    height: 20px;
    width: 20px;
    font-size: 10px;
    margin-right: -8px;
  }
  ul li button:hover{
    border-color: red;
    color: red;
  }
</style>