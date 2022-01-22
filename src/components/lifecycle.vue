<template>
  <div>
    <p>trace message is {{traces}}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onUnmounted,
  onErrorCaptured,
  onRenderTracked,
  onActivated,
  onDeactivated,
} from "vue"

export default defineComponent({
  name: "Home",
  components: {
  },
  setup(){

    const traces = ref(new Array<string>());

    onBeforeMount(() => {
      console.log("onBeforeMount");
    });

    onMounted(() => {
      console.log("onMounted");
    });

    onBeforeUpdate(() => {
      console.log("onBeforeUpdate");
    });

    onBeforeMount(() => {
      console.log("onBeforeMount");
    });

    onUpdated(() => {
      console.log("onUpdated");
    });

    onUnmounted(() => {
      console.log("onUnmounted");
    });

    onErrorCaptured(() => {
      console.log("onErrorCaptured");
    });

    onRenderTracked(() => {
      console.log("onRenderTracked");
    });

    onActivated(() => {
      console.log("onActivated");
    });

    onDeactivated(() => {
      console.log("onDeactivated");
    });

    return{
      traces
    }
  }
});
</script>