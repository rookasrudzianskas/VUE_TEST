<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
<!--    <h3>You have {{todosCount}} todos</h3>-->
    <div>
      <input type="text" v-model="newTodoName" @keyup.enter="addTodo" placeholder="Add a todo">
    </div>

    <div>
      <ul>
        <li v-for="(todo, index) in todos" :key="todo.id">
          <span>{{ todo.name }}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref } from "vue"
export default {
  setup() {
    let newTodoName = ref('')
    let todos = ref([

    ])
    const swearwords = ['fart', 'butt hair', 'willy']

    function addTodo() {
      let newTodo = {
              id: Date.now(),
              name: newTodoName.value
            }
            todos.value.push(newTodo)
            newTodoName.value = ''
            }

            function deleteTodo(index) {
                  todos.value.splice(index, 1)
            }

    return {
      newTodoName,
      todos,
      addTodo,
      deleteTodo,
    }
  }



  // data() {
  //   return {
  //     newTodoName: '',
  //     todos: [
  //       {
  //         id: 1,
  //         name: 'One',
  //       },
  //
  //       {
  //         id: 2,
  //         name: 'Two',
  //       },
  //
  //       {
  //         id: 3,
  //         name: 'Three',
  //       },
  //     ],
  //     swearwords: ['fart', 'butt hair', 'willy']
  //   }
  // },
  // computed: {
  //   todosCount() {
  //     return this.todos.length
  //   }
  // },
  // methods: {
  //   addTodo() {
  //     let newTodo = {
  //       id: Date.now(),
  //       name: this.newTodoName
  //     }
  //     this.todos.push(newTodo)
  //     this.newTodoName = ''
  //   },
  //   deleteTodo(index) {
  //     this.todos.splice(index, 1)
  //   }
  // },
  // watch: {
  //   newTodoName(newValue) {
  //     if(this.swearwords.includes(newValue.toLowerCase())) {
  //       this.newTodoName = ''
  //       alert("You must never say " + newValue + '!')
  //     }
  //   }
  // }
}
</script>

<style>
ul {
  list-style: none;
  padding: 0;
  width: 200px;
  margin: 20px auto 0;
}

li {
  border: 1px solid;
  display: flex;
  margin-bottom: 10px;
}

li span {
  flex-grow: 1;
}
</style>
