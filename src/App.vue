<template>
  <Nav />
  <div class="container">
    <h1>{{ title }}</h1>
    <div class="todo">
      <input
        type="text"
        :placeholder="placeholder"
        v-model="inputValue"
        @keypress.enter="addList"
      />

      <button class="btn" @click="addList">Add</button>
    </div>

    <ul class="list" v-if="lists.length !== 0">
      <li class="list-item" v-for="(todoItem, index) of lists" :key="index">
        {{ index + 1 }})
        {{ todoItem }}
        <button class="del" @click="delList(index)">Delete</button>
      </li>
      <hr />
      <p class="total">Total: {{ lists.length }}</p>
    </ul>
    <p class="no_lists" v-else>Add your list</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "ToDo list",
      placeholder: "Enter todo-item",
      inputValue: "",
      lists: [],
    }
  },
  methods: {
    addList() {
      if (this.inputValue !== "") {
        this.lists.push(this.inputValue)
        this.inputValue = ""
      }
    },
    delList(index) {
      this.lists.splice(index, 1)
    },
  },
}
</script>

<style>
* {
  outline: none;
  user-select: none;
  box-sizing: border-box;
  list-style: none;
}
.container {
  width: 1200px;
  margin: 0 auto;
}
h1 {
  font-size: 28px;
  color: #7b68ee;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}
.todo {
  border: 2px solid #00ffff;
  border-radius: 4px;
}
input {
  margin: 20px;
  padding: 6px;
  width: 50%;
  border: 1px solid #00ced1;
  color: #00ced1;
  border-radius: 3px;
}
button {
  padding: 6px;
  background: #4682b4;
  color: #fff;
  cursor: pointer;
  border-radius: 3px;
  border: none;
  width: 56px;
}
.list-item {
  padding: 10px;
  color: #40e0d0;
  font-family: cursive;
  font-style: italic;
}
.no_lists {
  color: #b0e0e6;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-style: italic;
}
.total {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  color: #1e90ff;
}
</style>
