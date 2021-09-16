<template>
  <div>
    <h1>App 根組件 </h1>

    <hr />
    <!-- 使用 TodoInput -->
    <todo-input @add='onAddNewTask'></todo-input>


    <!-- 使用 todo-list 組件 -->
    <todo-list :list="tasklist" class="mt-2"></todo-list>

    <!-- 使用 todo-button 組件 -->
    <todo-button v-model:active="activeBtnIndex" ></todo-button>
  </div>
</template>

<script>
// 導入 TodoList 組件
import TodoList from './components/todo-list/TodoList.vue'
// 導入 TodoInput 組件
import TodoInput from './components/todo-input/TodoInput.vue'
// 導入 TodoButton 組件
import TodoButton from './components/todo-button/TodoButton.vue'

export default {

  name: 'MyApp',
  data() {
    return {
      // task list data
      todolist: [
        { id: 1, task: '食飯飯', done: false },
        { id: 2, task: '睡覺覺', done: false },
        { id: 3, task: '寫代碼', done: true },
      ],
      // 下一個可用 ID
      nextId: 4,
      activeBtnIndex: 0,
    }
  },

  computed: {
    tasklist() {
      switch(this.activeBtnIndex) {
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter(x => x.done === true)
        case 2:
          return this.todolist.filter(x => x.done !== true)

      }
    }
  },

  methods:{
    onAddNewTask(taskname) {
      this.todolist.push({
        id: this.nextId,
        task: taskname,
        done: false
      })

      this.nextId++
    },
  },

  components: {
    TodoList, TodoInput, TodoButton
  }
}
</script>

<style lang="less" scoped>

</style>