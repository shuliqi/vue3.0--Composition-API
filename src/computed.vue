<template>
  <div>computed</div>
</template>
<script>
import { ref, computed, isRef } from "vue";
export default {
  setup () {
    const age = ref(0);
    // computed函数的返回值是响应式的ref对象
    const myComputedAge = computed(() => age.value + 1);
    console.log(isRef(myComputedAge), myComputedAge.value); // true 1

    // omputed函数的返回值是不可改变的
    myComputedAge.value = 3; //  Write operation failed: computed value is readonly
  }
}
</script>