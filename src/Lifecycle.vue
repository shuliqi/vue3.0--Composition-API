<teamlate>
</teamlate>
<script>
  import { 
    onBeforeMount,
    onMounted,
    onBeforeUpdate,
    onUpdated,
    onBeforeUnmount,
    onUnmounted,
    onErrorCaptured, 
    onRenderTracked,
    onRenderTriggered
 }  from "vue";
  export default {
    beforeCreate () {
      console.log("beforecreate")
    },
    created () {
      console.log("created")
    },
    setup () {
      onBeforeMount(() => {
        console.log("Composition API: onBeforeMount")
      });

      onMounted(() => {
        console.log("Composition API: onMounted")
      });

      onBeforeUpdate(() => {
        console.log("Composition API: onBeforeUpdate")
      })
      // ...

    },
    // ...
  }
</script>