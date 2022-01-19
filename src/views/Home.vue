<template>
  <Parent />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Parent from "../components/parenttop.vue";

export default defineComponent({
  name: "Home",
  components: {
    Parent
  },
});
</script>
