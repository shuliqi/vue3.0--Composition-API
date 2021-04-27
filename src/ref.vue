<template>
  <h4>ref</h4>
  <p>名字：{{}} </p>
</template>
<script>
import { ref }  from "vue";
export default {
  setup() {
    // ref 函数返回一个响应式
    const sex = ref("女");    // { value: "女"}
    console.log("sex", sex); 

    const isOk = ref(false);  // { value:  false }
    console.log("isOk", isOk); 

    const tag = ref(null);    // { value: null }
    console.log("tag", tag); 

    const people = ref({      // { value: { name: "shuliqi", age: 12 }}
      name:  "shuliqi",
      age: 12
    });
    console.log("people", people); 
    setTimeout(() => {
        // 修改变量需要修改对象的value值
        people.value.name = "zhangdada";
        console.log("更新后的people", people)
    });

    return  {

    }
  }
}
</script>