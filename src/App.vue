<template>
  <div class="parent">
    <p>Parent</p>
    <div>
      <span v-for="state in localStatus">{{
        `(${state.index})` + " ⇒ " + state.isBottomModal + ", "
      }}</span>
    </div>
  </div>
  <ChildComponent
    :local-status="localStatus"
    @on-toggle="onToggleTargetIsBottomoModal"
  />
</template>

<script>
import ChildComponent from "./components/ChildComponent.vue";
export default {
  name: "App",
  components: {
    ChildComponent,
  },
  data() {
    return {
      screenEvent: "",
      localStatus: [],
    };
  },
  created: function () {
    const arr = [0, 1, 2].map((_, index) => {
      return {
        index,
        isReverse: false,
        isBottomModal: false,
      };
    });

    this.localStatus = arr;
  },
  methods: {
    onToggleTargetIsBottomoModal(i) {
      this.localStatus[i].isBottomModal = !this.localStatus[i].isBottomModal;
    },
  },
};
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.parent {
  border: 1px solid #42b883aa;
  margin-bottom: 8px;
}
</style>
