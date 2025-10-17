<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Li Interface
   */
  interface LiAttributes {
    html?: string
    id?: string
  }

  /**
   * Ol Interface
   */
  interface OlAttributes {
    id?: string
    tabindex?: number | string
    li?: LiAttributes[]
    reversed?: boolean
    start?: number
    type?: "a" | "A" | "i" | "I" | "1"
  }

  /**
   * Ol Props
   */
  const props = defineProps<{
    attributes: OlAttributes
  }>()

  /**
   * Default Ol Attributes
   */
  const defaultAttributes: Partial<OlAttributes> = {
    id: undefined,
    tabindex: undefined,
    li: [],
    reversed: false,
    start: undefined,
    type: "1"
  }

  /**
   * Ol Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <ol
    class="ol"
    :id="attributes.id"
    :tabindex="attributes.tabindex"
    :reversed="attributes.reversed"
    :start="attributes.start"
    :type="attributes.type"
  >
    <li
      v-for="elem in attributes.li"
      :key="elem.id ?? elem.html"
      :id="elem.id"
      v-html="elem.html"
    >
    </li>
  </ol>
</template>

<style scoped>
  .ol {
    margin: 10px 0;
  }
</style>