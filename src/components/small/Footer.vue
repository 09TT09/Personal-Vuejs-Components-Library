<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Footer Interface
   */
  interface FooterAttributes {
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Footer Props
   */
  const props = defineProps<{
    attributes?: FooterAttributes
  }>()

  /**
   * Default Footer Attributes
   */
  const defaultAttributes: Partial<FooterAttributes> = {
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Footer Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <footer
    class="footer"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
  >
    <slot />
  </footer>
</template>

<style scoped>
</style>
