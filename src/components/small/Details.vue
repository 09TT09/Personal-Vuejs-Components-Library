<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Summary Interface
   */
  interface SummaryAttributes {
    id?: string
    text?: string
  }

  /**
   * Details Interface
   */
  interface DetailsAttributes {
    ariaLabel?: string
    id?: string
    open?: boolean
    summary?: SummaryAttributes
    tabindex?: number | string
  }

  /**
   * Details Props
   */
  const props = defineProps<{
    attributes: DetailsAttributes
  }>()

  /**
   * Default Details Attributes
   */
  const defaultAttributes: Partial<DetailsAttributes> = {
    ariaLabel: undefined,
    id: undefined,
    open: false,
    summary: undefined,
    tabindex: undefined,
  }

  /**
   * Details Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <details
    class="details"
    :aria-label="attributes.ariaLabel"
    :id="attributes.id"
    :open="attributes.open"
    :tabindex="attributes.tabindex"
  >
    <summary v-if="attributes.summary" :id="attributes.summary.id" class="details-summary">
      {{ attributes.summary.text }}
    </summary>
    <div class="details-content">
      <slot />
    </div>
  </details>
</template>

<style scoped>
</style>
