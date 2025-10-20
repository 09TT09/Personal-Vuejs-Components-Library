<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Section Interface
   */
  interface SectionAttributes {
    ariaLabel?: string
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Section Props
   */
  const props = defineProps<{
    attributes?: SectionAttributes
  }>()

  /**
   * Default Section Attributes
   */
  const defaultAttributes: Partial<SectionAttributes> = {
    ariaLabel: undefined,
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Section Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <section
    class="section"
    :aria-label="attributes.ariaLabel"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
  >
    <slot />
  </section>
</template>

<style scoped>
</style>
