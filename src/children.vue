<template>
  <button @click="onInitName">重新初始名字</button>
  <p>
    名字：{{ name }}
    年龄： {{ myAge }}
  </p>
  <p>
  </p>
 
</template>
<script>
  import { toRefs } from "vue";
  export default {
    props: {
      name: String,
      age: Number
    },
    // 必要要在 emits 中中把父组件传的函数写上
    emits: ["updateName"],
    setup (props, context) {
      // ES6 解构并且保持数据的响应性，可以使用 toRefs 来完成
      const { age: myAge  } = toRefs(props);

      const onInitName = () => {
        // 触发父组件的方法
        context.emit("updateName", "我是初始化的名字")
      }
      return {
        myAge,  // 具有响应性的数据
        onInitName
      }

    }
  }
</script>]