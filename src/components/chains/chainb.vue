<template>
  <div>
    <chainc :likes="likes" @cclick="increment"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import chainc from "./chainc.vue";

export default defineComponent({
  name: "chainb",
  components: {
    chainc
  },
  props: {
    likes: {
      type: Number,
      default: 0
    }
  },
  emits: ["bclick"],
  setup(_, context) {

    const increment = (val: number) => {
      context.emit("bclick", val);
    };
    return {
      increment
    };
  },
});
</script>

<style scoped>
</style>
