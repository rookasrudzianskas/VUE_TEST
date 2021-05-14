<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h3>You have XXX todos</h3>
    <div>
      <input type="text" placeholder="Add a todo">
    </div>

    <div>
      <ul>
        <li>
          <span>One</span>
          <button>X</button>
        </li>

        <li>
          <span>Two</span>
          <button>X</button>
        </li>

        <li>
          <span>Three</span>
          <button>X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      todos: [
        {
          id: 1,
          name: 'One',
        },

        {
          id: 2,
          name: 'Two',
        },

        {
          id: 3,
          name: 'Three',
        },
      ]
    }
  }
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
