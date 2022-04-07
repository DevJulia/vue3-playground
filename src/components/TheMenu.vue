<script setup lang="ts">
import MenuItem from "./MenuItem.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
</script>

<template>
  <div>
    <MenuItem title="To do list" :to="{ name: 'home' }">
      <template #icon>
        <font-awesome-icon :icon="['far', 'rectangle-list']" />
      </template>
    </MenuItem>

    <MenuItem title="CSS features" :to="{ name: 'about' }">
      <template #icon>
        <ToolingIcon />
      </template>
    </MenuItem>

    <MenuItem title="Pinia" :to="{ name: 'about' }">
      <template #icon>
        <EcosystemIcon />
      </template>
    </MenuItem>

    <MenuItem :to="{ name: 'about' }">
      <template #icon>
        <CommunityIcon />
      </template>
    </MenuItem>

    <MenuItem :to="{ name: 'about' }">
      <template #icon>
        <SupportIcon />
      </template>
    </MenuItem>
  </div>
</template>
