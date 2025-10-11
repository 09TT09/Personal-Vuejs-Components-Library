<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Span Interface
   */
  interface SpanAttributes {
    html: string
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Span Props
   */
  const props = defineProps<{
    attributes?: SpanAttributes
  }>()

  /**
   * Default Span Attributes
   */
  const defaultAttributes: Partial<SpanAttributes> = {
    html: undefined,
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
  }

  /**
   * Span Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <span
    class="span"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
    v-html="attributes.html"
  ></span>
</template>

<style scoped>
</style>
