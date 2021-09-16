<template>
  <ul class="list-group">
    <!-- 列表組 -->
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in list" :key="item.id">
        <!-- CheckBox -->
        <div class="form-check">
            <input class="form-check-input" type="checkbox" :id="item.id" v-model="item.done" />
            <label class="form-check-label" :class="item.done ? 'delete' : '' " :for="item.id">{{item.task}}</label>
        </div>
        <!-- 標示 -->
        <span class="badge bg-success rounded-pill" v-if="item.done">已完成</span>
        <span class="badge bg-warning rounded-pill" v-else>未完成</span>
    </li>
</ul>
</template>

<script>
export default {
    name: 'TodoList',
    props: {
        list: {
            type: Array,
            required: true,
            default: [],
        },
    },
}
</script>

<style lang="less" scoped>
.list-group {
    width: 350px;
}

.delete {
    text-decoration: line-through;
    color: grey;
    font-style: italic;
}

</style>