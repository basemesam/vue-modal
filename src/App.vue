<template>
  <h1>{{ title }}</h1>

  <div style="margin-bottom: 20px">
    <input type="text" ref="name" />
    <button @click="handleClick">Click</button>
  </div>

  <teleport to=".modals" v-if="showModal">
    <Modal @close="toggleModal" theme="sale">
      <template v-slot:links>
        <a href="#">Click 1</a>
        <a href="#">Click 2</a>
      </template>

      <h1>Content Header</h1>
      <p>Lorem ipsum</p>
    </Modal>
  </teleport>

  <button @click="toggleModal">Toggle Modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Hello vue :)",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app,
.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
