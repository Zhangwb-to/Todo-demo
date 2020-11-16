<template>
  <main>
    <div class="container">
      <h1>欢迎使用Todo!</h1>
      <todo-add :tid="todos.length" @add-todo="addTodo"/>
      <todo-filter :selected="filter" @change-filter="filter = $event" />
      <todo-list :todos="filteredTodos"/>
    </div>
  </main>
</template>

<script>
import TodoAdd from '@/components/TodoAdd'
import TodoFilter from '@/components/TodoFilter'
import TodoList from '@/components/TodoList'
import useTodos from "@/composables/useTodos"
import useFiltersTodo from '@/composables/useFiltersTodo'

export default {
  name: 'App',
  components: {
    TodoAdd,
    TodoFilter,
    TodoList
  },
  setup() {
    const { todos, addTodo } = useTodos();
    const { filter, filteredTodos } = useFiltersTodo(todos);
    return {
      todos,
      addTodo,
      filter,
      filteredTodos
    }
  }
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Helvetica, "PingFang SC", "Microsoft Yahei", sans-serif;
}
main {
  width: 100vw;
  min-height: 100vh;
  display: grid;
  align-items: center;
  justify-items: center;
  background-color: rgb(203,210,240);
}
.container {
  width: 94%;
  max-width: 400px;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.15);
  padding: 48px 24px;
  border-radius: 12px;
  background-color: rgb(245, 246, 252);
}

/* 标题 */
h1 {
  margin: 26px 0;
  font-size: 28px;
  color: #414873;
}

</style>
