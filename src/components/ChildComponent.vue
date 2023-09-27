<template>
  <div class="child">
    <p>Child</p>

    <p>
      Check out
      <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
        >create-vue</a
      >, the official Vue + Vite starter
    </p>
    <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  </div>

  <GrandChildComponent :local-status="localStatus" @on-toggle="onClickToggle" />
</template>

<script>
import GrandChildComponent from "./GrandChildComponent.vue";
export default {
  name: "ChildComponent",
  components: {
    GrandChildComponent,
  },
  props: {
    localStatus: {
      type: Array,
    },
  },
  methods: {
    onClickToggle(eventIndex) {
      this.$emit("on-toggle", eventIndex);
    },
  },
};
</script>

<style scoped>
.read-the-docs {
  color: #888;
}

.child {
  border: 1px solid #888;
  margin-bottom: 8px;
  padding: 0 8px;
}
</style>
