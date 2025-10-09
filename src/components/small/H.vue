<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * H Interface
   */
  interface HAttributes {
    elementtiming?: string
    id?: string
    html?: string
    level?: "h1" | "h2" | "h3" | "h4" | "h5" | "h6"
  }

  /**
   * H Props
   */
  const props = defineProps<{
    'attributes': HAttributes
  }>()

  /**
   * Default H Attributes
   */
  const defaultAttributes: Partial<HAttributes> = {
    elementtiming: undefined,
    id: undefined,
    html: undefined,
    level: "h1",
  }

  /**
   * H Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <component
    class="h"
    :elementtiming="attributes.elementtiming"
    :id="attributes.id"
    :is="attributes.level"
    v-html="attributes.html"
  />
</template>

<style scoped>
  .h {
    margin: 0;
  }
</style>