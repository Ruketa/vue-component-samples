<template>
  <div>
    <button @click="click">{{likes}}</button> 
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "grandchild",
  props: {
    likes: {
      type: Number,
      default: 0
    }
  },
  emits: ["dclick"],
  setup(props, { emit }) {
    const click = () => {
      emit("dclick", props.likes + 1);
    };
    return {
      click
    }
  }
});
</script>