
<template>
  <div>readonly</div>
  <p>name: {{ readonlyName }}</p>
  <p>state: {{ readonlyState.title }}</p>
</template>
<script>
  import { ref, readonly, reactive } from "vue";
  export default {
    setup () {
      // readonly 一个 ref 对象
      const name = ref("shuliqi");
      const readonlyName = readonly(name);
      console.log("读取只读代理的值：",readonlyName.value );
      // 尝试修改会直接警告
      readonlyName.value = "张大大"; // Set operation on key "value" failed: target is readonly.
      setTimeout(() => {
        name.value = "小小舒";
        console.log("原始ref对象改变，只读代理的值也会变：",readonlyName.value)
      }, 3000)

      // readonly 一个 reactive 对象
      const state  = reactive({
        title: "标题",
        subTitle: "二级标题"
      })
      const readonlyState = readonly(state);
      console.log("读取只读代理的值(reactive)：",readonlyState.title );
      // 尝试修改会直接警告
      readonlyState.title = "修改标题"; // Set operation on key "title" failed: target is readonly

      setTimeout(() => {
        state.title = "标题被修改了";
        console.log("原始reactive对象改变，只读代理的值也会变(reactive)：",readonlyState.title);
      }, 3000)

      // readonly 一个普调对象
      const obj = {
        size: 12,
        isNew: true,
      }
      const readonlyObj = readonly(obj);
      console.log("读取readonly一个普调对象的只读代理的值：",readonlyObj );
      //  尝试修改 readonlyObj, 直接警告
      readonlyObj.size = 100;  // Set operation on key "size" failed: target is readonly
      //  修改原始数据
      obj.size = 3000;
      console.log("原始数据obj改变， readonlyObj也会改变",  readonlyObj); // { size: 3000, isNew: true }

      // readonly 一个非对象: 就不具有只读特性了
      const str = "oldDate";
      let readonlyStr = readonly(str);
      console.log("readonlyStr:",readonlyStr)
      // 可以直接修改，说明不具有只读特性
      readonlyStr = "newDate";
      console.log("newReadonlyStr:",readonlyStr)

      return {
        // 具有响应性
        readonlyName, 
        readonlyState
      }

    }
  }
</script>
