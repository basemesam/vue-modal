<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot></slot>

      <div class="action">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Modal",
  props: ["theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.modal {
  width: 400px;
  padding: 20px;
  margin: 200px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  left: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  font-weight: 500;
  color: #f00;
}
.modal p {
  font-style: normal;
}
.modal.sale {
  background-color: #f00;
  color: white;
}

.modal.sale h1 {
  color: white;
}
</style>
