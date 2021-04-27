<template>
 <p> reactive </p>
 <p>名字：{{ name }} </p>
 <p>年龄：{{ name }} </p>
 <p>性别：{{ sex }} </p>
</template>
<script>
import { reactive, toRefs }  from "vue";
export default {
  setup() {
    // 使用 reactive 初始化一个变量
    const state = reactive({
      name: "shuliqi",
      age: 12,
      sex: "女"
    }) 
    console.log("reactive", state)
    setTimeout(() => {
        // reactive 中的变量 的取值和赋值不需要 取其 value 属性
        state.name = "更改之后的名字";
        console.log("更新后的state的name值:", state.name)
    }, 2000);

    return  {
      // ...state  会失去响应性
      ...toRefs(state) // 会保留响应性
    }
  }
}
</script>