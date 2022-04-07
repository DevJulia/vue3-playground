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
  <RouterLink :to="to" class="item">
    <i class="tooltip-toggle" :aria-label="title" tabindex="0">
      <slot name="icon"></slot>
    </i>
  </RouterLink>
</template>

<style scoped lang="scss">
.tooltip-toggle {
  cursor: pointer;

  //Tooltip text container
  &::before {
    position: absolute;
    top: 0rem;
    left: 52px;
    background-color: #2b222a;
    border-radius: 5px;
    color: #fff;
    padding: 0.5rem;
    width: 15ch;
    content: attr(aria-label);
    transition: all 0.5s ease;
  }

  &::before {
    color: #efefef;
    opacity: 0;
    pointer-events: none;
    text-align: center;
  }

  &:hover::before {
    opacity: 0.5;
    transition: all 0.75s ease;
  }
}

.item {
  display: block;
  margin-top: 2rem;
  padding: 0.4rem 0 1rem calc(var(--section-gap) / 2);

  &:hover {
    i {
      background-color: hsla(160, 100%, 37%, 0.2);
    }
  }
}

i {
  display: flex;
  place-items: center;
  place-content: center;

  color: var(--color-text);
  top: calc(50% - 25px);
  left: -26px;
  position: absolute;
  border: 1px solid var(--color-border);
  background: var(--color-background);
  border-radius: 8px;
  width: 50px;
  height: 50px;
}
</style>
