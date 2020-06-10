<template>
  <div class="todos">
    <h1>Todo App</h1>

    <input @keyup.enter="addTodo" type="text" v-model="title" placeholder="What you want to do?">
    <button @click="addTodo">Add to list</button>

    <ul>
      <li v-bind:key="(todo, index)" v-for="(todo, index) in todos">{{todo}}
      <span @click="remove(index)" class="remove">x</span>
      </li>
    </ul>

  </div>
</template>


<script>
export default {
  name: "todo",
  props: {
    msg: String
  },

  data(){
    return{
      title: '',
      todos: [
        'Go home',
      ]
    }
  },

  methods: {
    addTodo(){
      if(this.title != ''){
      this.todos.unshift(this.title);
      this.title = "";
      }
    },
    remove(id){
      // console.log(id);
      // this.todos.splice(id,1)
      this.$delete(this.todos, id);
    }
  }

};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.remove{
  padding: .3rem .6rem;
  background-color: crimson;
  color: #fff;
  border-radius: 30px;
}

.remove:hover{
  cursor: pointer;
}

ul li {
  padding: .4rem;
}

</style>
