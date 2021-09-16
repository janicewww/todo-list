<template>
  <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="onFormSubmit" >
  <div class="col-12">
    <div class="input-group">
      <div class="input-group-text">Task</div>
      <input type="text" class="form-control" placeholder="What is your task today?" v-model="taskname" />
    </div>
  </div>


  <div class="col-12">
    <button type="submit" class="btn btn-primary">Add</button>
  </div>
</form>
</template>

<script>
export default {
    name: 'TodoInput',
    emits: ['add'],
    data() {
      return {
        taskname: ''
      }
    },
    methods: {
      // 表單的提交事件
      onFormSubmit() {
        if(!this.taskname) return alert('Please input your task!')
        this.$emit('add', this.taskname)
        this.taskname = ''
      }
    }

}
</script>

<style lang="less" scoped>
  .input-group {
    width: 250px;
  }



</style>