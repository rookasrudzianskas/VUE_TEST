<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h3>You have {{todosCount}} todos</h3>
    <div>
      <input type="text" v-model="data.newTodoName" @keyup.enter="addTodo" placeholder="Add a todo">
    </div>

    <div>
      <ul>
        <li v-for="(todo, index) in data.todos" :key="todo.id">
          <span>{{ todo.name }}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref, computed, watch, reactive } from "vue"
export default {
  setup() {
    let newTodoName = ref('')
    let todos = ref([

    ])

    let data = reactive({
      newTodoName: '',
      todos: [],
    })
    const swearwords = ['fart', 'butt hair', 'willy']

    let todosCount = computed(() => {
      return data.todos.length
    })

    function addTodo() {
      let newTodo = {
              id: Date.now(),
              name: data.newTodoName
            }
            data.todos.push(newTodo)
            data.newTodoName = ''
            }

            function deleteTodo(index) {
                  data.todos.splice(index, 1)
            }

            watch(newTodoName, (newValue) => {
              if(swearwords.includes(newValue.toLowerCase())) {
                      newTodoName.value = ''
                      alert("You must never say " + newValue + '!')
                    }
            })

    return {
      newTodoName,
      todos,
      addTodo,
      deleteTodo,
      todosCount,
      data,

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
