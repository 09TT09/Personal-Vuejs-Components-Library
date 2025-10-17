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
   * Ul Interface
   */
  interface UlAttributes {
    id?: string
    tabindex?: number | string
    li?: LiAttributes[]
  }

  /**
   * Ul Props
   */
  const props = defineProps<{
    attributes: UlAttributes
  }>()

  /**
   * Default Ul Attributes
   */
  const defaultAttributes: Partial<UlAttributes> = {
    id: undefined,
    tabindex: undefined,
    li: []
  }

  /**
   * Ul Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <ul
    class="ul"
    :id="attributes.id"
    :tabindex="attributes.tabindex"
  >
    <li
      v-for="elem in attributes.li"
      :key="elem.id ?? elem.html"
      :id="elem.id"
      v-html="elem.html"
    >
    </li>
  </ul>
</template>

<style scoped>
  .ul {
    margin: 10px 0;
  }
</style>