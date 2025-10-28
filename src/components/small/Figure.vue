<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Figcaption Interface
   */
  interface FigcaptionAttributes {
    id?: string
  }

  /**
   * Figure Interface
   */
  interface FigureAttributes {
    figcaption?: FigcaptionAttributes
    id?: string
    tabindex?: number | string
  }

  /**
   * Figure Props
   */
  const props = defineProps<{
    attributes: FigureAttributes
  }>()

  /**
   * Default Figure Attributes
   */
  const defaultAttributes: Partial<FigureAttributes> = {
    id: undefined,
    tabindex: undefined,
    figcaption: undefined,
  }

  /**
   * Figure Computed attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <figure
    class="figure"
    :id="attributes.id"
    :tabindex="attributes.tabindex"
  >
    <slot></slot>
    <figcaption
      v-if="attributes.figcaption"
      class="figcaption"
      :id="attributes.figcaption.id"
    >
      <slot name="figcaption"></slot>
    </figcaption>
  </figure>
</template>

<style scoped>
</style>
