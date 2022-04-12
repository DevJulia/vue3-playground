<script setup>
defineProps({
  title: {
    type: String,
    default: "An app",
    validator(value) {
      return value.length <= 15;
    },
  },
  to: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <RouterLink :to="to" class="menu-item" :title="title">
    <slot name="icon"></slot>
  </RouterLink>
</template>

<style scoped lang="scss">
.menu-item {
  border: 1px solid var(--color-border);
  border-radius: 8px;
  display: flex;
  place-content: center;
  place-items: center;
  height: 50px;
  width: 50px;
  margin: 5px 0;
  background: var(--color-background);
  transition: background 0.25s;
  color: var(--color-text);

  &:hover {
    background-color: hsla(160, 100%, 37%, 0.4) !important;
  }

  &.router-link-active {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}
</style>
