<template>
    <div class="todo-list">
        <h2>{{ category }}</h2>
        <input type="text" v-model="newTodo" @keyup.enter="addTodo"><br>
        <button @click="addTodo(todos)">추가</button>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.content }}
            <button @click="removeTodo(todo.id)">삭제</button>
        </li>
    </div>

</template>

<script>
export default {
    props: {
      category: {
        type: String,
        required: true
      }
    }, // 하위컴포너트로 데이터 전송 + 검증
    data: function () {
      return {
        todos: [],
        newTodo: ''
      }
    },
    methods: {
      addTodo: function () {
        this.todos.push({
          id: Date.now(),
          content: this.newTodo,
        })
        this.newTodo = ''
      },
      removeTodo(todoId) {
        this.todos = this.todos.filter(function (todo) {
          return todo.id !== todoId
        })
      }
    }
  }

</script>

<style lang="">
    /* li {
        color: blue;
    } */
</style>