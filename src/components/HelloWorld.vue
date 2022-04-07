<script setup lang="ts">
defineProps<{
  msg: string;
}>();
</script>

<template>
  <div class="greetings">
    <h1 class="green">
      <img
        alt="Vue logo"
        class="logo"
        src="@/assets/logo.svg"
        width="60"
        height="60"
      />{{ msg }}
    </h1>
    <h3>Now let's play, click on one of the icons to discover some usecase.</h3>
  </div>
</template>

<style scoped>
.logo {
  display: block;
}

h1 {
  font-weight: 500;
  font-size: 2rem;
  top: -10px;
  line-height: 1;
  display: flex;
  column-gap: 0.5rem;
  place-items: center;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
