<script setup lang="ts">
import MenuItem from "./MenuItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
</script>

<template>
  <div>
    <MenuItem title="Documentation" :to="{ name: 'home' }">
      <template #icon>
        <DocumentationIcon />
      </template>
    </MenuItem>

    <MenuItem :to="{ name: 'about' }">
      <template #icon>
        <ToolingIcon />
      </template>
    </MenuItem>

    <MenuItem :to="{ name: 'about' }">
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
