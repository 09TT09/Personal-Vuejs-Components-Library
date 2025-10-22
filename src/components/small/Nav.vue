<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Nav Interface
   */
  interface NavAttributes {
    ariaLabel?: string
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Nav Props
   */
  const props = defineProps<{
    attributes?: NavAttributes
  }>()

  /**
   * Default Nav Attributes
   */
  const defaultAttributes: Partial<NavAttributes> = {
    ariaLabel: undefined,
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Nav Computed attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <nav
    class="nav"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
    :aria-label="attributes.ariaLabel"
  >
    <slot />
  </nav>
</template>

<style scoped>
</style>
