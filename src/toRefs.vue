<template>
  <h3>toRefs</h3>
</template>
<script>
import { toRefs, reactive, isRef } from "vue";
export default {
  setup (){
    const people = reactive({
      age: 12,
      sex: "女"
    });
    const { age, sex } = toRefs(people);
    console.log(isRef(age), isRef(sex)) // true true
    console.log(age.value, sex.value) // 12 shuliqi
  }
}
</script>