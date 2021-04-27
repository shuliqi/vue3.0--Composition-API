<template>
<div></div>
</template>
<script>
  import { watch, ref, reactive } from "vue";
  export default {
    setup () {
      // 监听`ref`定义的数据
      const name = ref("shuliqi");
      setTimeout(() => {
        name.value = "张大大";
      }, 1000);
      watch(name, (newName,oldName) => {
        console.log("发生了变化：", "newName:", newName, "oldName:", oldName )
      })

      // 监听`reactive`定义的数据
      const  obj = reactive({
        name: "shuliqi",
        age: 12
      })
      setTimeout(() => {
        obj.name = "张大大"
      }, 500)
      watch(() => obj.name, (newName,oldName) => {
        console.log("发生了变化：", "newName:", newName, "oldName:", oldName)
      })

      // 监听多个数据源
      const age = ref(12);
      const sex = ref("女");
      setTimeout(() => {
        sex.value = "男";
      })
      watch([age, sex], (newName,oldName) => {
        console.log("发生了变化：", "newName", newName, "oldName", oldName)
      })

      // 监听复杂的嵌套数据
      const state = reactive({
        total: 12,
        data: {
          titile: "标题",
          result: {
            nane: "shuliqi",
            age: 12
          }
        }
      });
      setTimeout(() => {
        state.data.result.name = "张大大";
      }, 500)
      watch(() => state.data, (newName,oldName) => {
        console.log("发生了变化：", "newName:", newName, "oldName:", oldName)
      },  {
        deep: true
      })


      // 设置`watch`为立即执行
      const  mySex = ref("女");
      watch(mySex, (newName, oldName) => {
        console.log("我不是惰性的：", "newName:", newName, "oldName:", oldName)
      }, { immediate: true })
  

      // 停止监听
      const myage = ref(12);
      const stop = watch(myage, (newName, oldName) => {
         console.log("我不是惰性的：", "newName:", newName, "oldName:", oldName)
      });
      stop();
      setTimeout(() => {
        myage.value = 27;
      }, 3000)


      {
        // 不能监听非响应式的值
        let age = 0;
        setTimeout(() => {
          age++;
          console.log("改变值", age);

        }, 1000);
        watch(() => age, () => {
          console.log("asdas");
        })
      }
    }

  }
</script>