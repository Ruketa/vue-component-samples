<template>
  <div>
    <h1>Parent</h1>
    <child class="child" title="Push!!" :start="start" @increment="increment">
      <!--slotへの設定がない場合はデフォルト値が設定される-->
    </child>
    <child class="child" title="Push!!" :start="start" @increment="increment">
      <!--slotで挿入される-->
      {{childSlot}}
    </child>

    <p>total increment count is {{total}}</p>

    <base-layout>
      <template v-slot:header>
        <h1>Header part</h1>
      </template>
      <template v-slot:default>
        <h1>Default part</h1>
      </template>
      <template v-slot:footer>
        <h1>Footer part</h1>
      </template>
    </base-layout>

    <div>
      <h1>Component chains</h1>
      <chaina :likes="likes" @aclick="incrementLikes"/>
      <p> likes is {{likes}}</p>
    </div>

    <div>
      <button @click="toggleShow">toggleBuild</button>
      <lifecycle v-if="show" />
      <br/>
      <button @click="toggleVisible">toggleVisible</button>
      <lifecycle v-show="visible" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import baseLayout from "./baselayout.vue";
import chaina from "./chains/chaina.vue";
import child from "./child.vue"
import lifecycle from "./lifecycle.vue";

export default defineComponent({
  name: "parent",
  components: {
    chaina, 
    child,
    "base-layout": baseLayout,
    lifecycle
  },
  setup(){
    const start = ref(0);
    const total = ref(0);
    const childSlot= ref("My Child Title");
    const likes = ref(0);
    const show = ref(false);
    const visible = ref(false);
    const increment = () => {
      total.value++;
    };
    const incrementLikes = () => {
      likes.value++;
    };
    const toggleShow = () => {
      show.value = !show.value;
    };
    const toggleVisible = () => {
      visible.value = !visible.value;
    };

    return {
      start,
      total,
      likes,
      childSlot,
      show,
      visible,

      increment,
      incrementLikes,
      toggleShow,
      toggleVisible,
    }
  }
});
</script>
