<template>
  <h3>isRef</h3>
</template>
<script>
import { ref, reactive, isRef } from "vue";
export default {
  setup (){
    const name = ref("shuliqi");
    const people = reactive({
      age: 12,
      sex: "女"
    });
    console.log(isRef(name)); // true
    console.log(isRef(name) ? name.value : name); // shuliqi
    console.log(isRef(people)) // false
    console.log(isRef(people) ? people.value.age : people.age) // 12
  }
}
</script>