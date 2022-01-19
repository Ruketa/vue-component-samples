<template>
  <div>
    <h1>Parent</h1>
    <child class="child" title="Push!!" :start="start"></child>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import child from "./child.vue";

export default defineComponent({
  name: "parent",
  components: {
    child
  },
  setup(){
    const start = ref(0);
    return {
      start
    }
  }
});
</script>
