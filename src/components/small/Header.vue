<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Header Interface
   */
  interface HeaderAttributes {
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Header Props
   */
  const props = defineProps<{
    attributes?: HeaderAttributes
  }>()

  /**
   * Default Header Attributes
   */
  const defaultAttributes: Partial<HeaderAttributes> = {
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Header Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <header
    class="header"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
  >
    <slot />
  </header>
</template>

<style scoped>
</style>
