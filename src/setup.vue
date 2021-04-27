<template>
<div>setup</div>
</template>
<script>
export default {
  beforeCreate () {
    console.log("------beforeCreate------")
  },
  created () {
    console.log("------created------")
  },
  setup () {
    console.log("------setup------", this);
  }
}
</script>