<template>
  <input type="text" v-model="name">
  <p><button @click="addAge">加年龄</button></p>
  <children :name="name" 
            :age="age"
            @updateName="updateName">
  </children>
</template>

<script>
import { ref } from "vue";

import children from './children.vue'
// import refTemplate from "./ref";
// import reactiveTemplate from "./reactive";
export default {
  name: 'parent',
  components: {
    children
    // refTemplate,
    // reactiveTemplate
  },
  setup() {
    const name = ref("");
    const age = ref(0);
    const addAge = () => {
      ++age.value;
    }
    const updateName = (newName) => {
      name.value = newName
    }

    return { 
      name,
      age,
      addAge,
      updateName
      
    }
  }
}
</script>
