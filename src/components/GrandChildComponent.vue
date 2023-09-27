<template>
  <div class="grand-child">
    <p>GrandChild</p>

    <p>
      <button @click="eventNumber--" :disabled="eventNumber === 0">-</button>
      {{ `[ ${eventNumber} ]` }}
      <button
        @click="eventNumber++"
        :disabled="eventNumber > localStatus.length - 2"
      >
        +
      </button>
    </p>

    <p>
      <button @click="onClickToggle">Toggle target isBottomModal</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "GrandChildComponent",
  props: {
    localStatus: {
      type: Array,
    },
  },
  data() {
    return {
      eventNumber: 0,
    };
  },
  methods: {
    onClickToggle() {
      this.$emit("on-toggle", this.eventNumber);
    },
  },
};
</script>

<style scoped>
.grand-child {
  border: 1px solid #646cffaa;
}
</style>
