<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Label Interfaces
   */
  interface LabelAttributes {
    for?: string,
    html?: string
    id?: string
  }

  /**
   * Label Props
   */
  const props = defineProps<{
    'attributes': LabelAttributes
  }>()

  /**
   * Default Label Attributes
   */
  const defaultAttributes: Partial<LabelAttributes> = {
    for: undefined,
    html: undefined,
    id: undefined,
  }

  /**
   * Label Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <label
    class="label"
    :for="attributes.for"
    :id="attributes.id"
    v-html="attributes.html"
  >
  </label>
</template>

<style scoped>
</style>