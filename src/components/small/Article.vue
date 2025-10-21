<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Article Interface
   */
  interface ArticleAttributes {
    ariaLabel?: string
    id?: string
    role?: string
    tabindex?: number | string
    title?: string
  }

  /**
   * Article Props
   */
  const props = defineProps<{
    attributes?: ArticleAttributes
  }>()

  /**
   * Default Article Attributes
   */
  const defaultAttributes: Partial<ArticleAttributes> = {
    id: undefined,
    role: undefined,
    tabindex: undefined,
    title: undefined,
    ariaLabel: undefined,
  }

  /**
   * Article Computed attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <article
    class="article"
    :id="attributes.id"
    :role="attributes.role"
    :tabindex="attributes.tabindex"
    :title="attributes.title"
    :aria-label="attributes.ariaLabel"
  >
    <slot />
  </article>
</template>

<style scoped>
</style>
