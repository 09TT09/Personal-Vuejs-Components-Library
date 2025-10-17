<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * P Interface
   */
  interface PAttributes {
    elementtiming?: string 
    id?: string
    html?: string
  }

  /**
   * P Props
   */
  const props = defineProps<{
    attributes: PAttributes
  }>()

  /**
   * Default P Attributes
   */
  const defaultAttributes: Partial<PAttributes> = {
    elementtiming: undefined,
    id: undefined,
    html: undefined,
  }

  /**
   * P Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <p
    class="p"
    :elementtiming="attributes.elementtiming"
    :id="attributes.id"
    v-html="attributes.html"
  ></p>
</template>

<style scoped>
  .p {
    margin: 0;
  }
</style>