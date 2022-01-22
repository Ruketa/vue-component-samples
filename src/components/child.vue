<template>
  <div>
    <h1>
      <slot>Default Title</slot>
    </h1>
    <div class="hstack">
      <h3>{{ title }}</h3>
      <button class="item" @click="increment">likes</button> 
      <p class="item">{{count}} likes</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Child",
  components: {

  },
  props: {
    title: {
      type: String,
      required: true,
      default: "",
    }, 
    start: {
      type: Number,
      required: true,
      default: 0,
      validator: (value: number) => {
        return value >= 0;
      }
    },
  },
  emits: ["increment"],
  setup(props, context) {

    const count = ref(props.start)
    const increment = () => {
      count.value++;
      context.emit("increment", count.value);
    };

    return {
      count, increment
    };
  },
});
</script>

<style scoped>
.hstack {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.item {
  margin: 0.5rem;
}
</style>
