<template>
  <div>watchEffect</div>
</template>
<script>
import { ref, watchEffect } from "vue";
export default {
  setup () {
    const name = ref("shuliqi");
    const age = ref(0);
    setTimeout(() => {
      name.value = "张大大";
      age.value = 20;
    }, 1000);
    const stop = watchEffect(() => {
      console.log("name值：", name.value, "age值：", age.value);
    });
    // 停止监听
    stop();



    {
      // 不能监听非响应式的值
      let age = 0;
      setTimeout(() => {
        age++;
        console.log("改变值", age);

      }, 1000);
      watchEffect(() => age, () => {
        console.log("asdas");
      })
    }
  }
}
</script>