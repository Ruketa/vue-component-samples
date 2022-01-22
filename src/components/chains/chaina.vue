<template>
  <chainb :likes="likes"  @bclick="increment"/>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import chainb from "./chainb.vue"

export default defineComponent({
  name: "chaina",
  components: {
    chainb
  },
  props: {
    likes: {
      type: Number,
      default: 0
    }
  },
  emits: ["aclick"],
  setup(_, context) {

    const increment = (val: number) => {
      context.emit("aclick", val);
    };
    return {
      increment
    };
  },

});
</script>

<style scoped>
</style>
