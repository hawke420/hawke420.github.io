<template>
    <ul class="todo-main">
        <MyItem />
        <MyItem />
    </ul>
</template>
  
<script>
// 引入子组件
import MyItem from "@/components/MyItem";
export default {
    name: "MyList",
    components: { MyItem } // 注册子组件
}
</script>
  
<style scoped>
.todo-main {
    margin-left: 0;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0;
}

.todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
}
</style>