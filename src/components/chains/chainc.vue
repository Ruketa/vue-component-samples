<template>
  <div>
    <div>
      <chaind :likes="likes" @dclick="increment"/>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import chaind from "./chaind.vue";

export default defineComponent({
  name: "chainc",
  components: {
    chaind
  },
  props: {
    likes: {
      type: Number,
      default: 0
    }
  },
  emits: ["cclick"],
  setup(_, context) {

    const increment = (val: number) => {
      context.emit("cclick", val);
    };
    return {
      increment
    };
  },
});
</script>

<style scoped>
</style>
