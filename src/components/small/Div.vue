<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Div Interface
   */
  interface DivAttributes {
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Div Props
   */
  const props = defineProps<{
    attributes?: DivAttributes
  }>()

  /**
   * Default Div Attributes
   */
  const defaultAttributes: Partial<DivAttributes> = {
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Div Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <div
    class="div"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
  >
    <slot></slot>
  </div>
</template>

<style scoped>
</style>
