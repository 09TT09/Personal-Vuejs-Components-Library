<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * A Interface
   */
  interface AAttributes {
    download?: string
    href?: string
    id?: string
    referrerpolicy?: "no-referrer" | "no-referrer-when-downgrade" | "origin" | "origin-when-cross-origin" | "same-origin" | "strict-origin-when-cross-origin" | "unsafe-url"
    rel?: "alternate" | "author" | "bookmark" | "external" | "help" | "license" | "next" | "nofollow" | "noreferrer" | "noopener" | "prev" | "search" | "tag"
    tabindex?: number | string
    target?: "_blank" | "_parent" | "_self" | "_top"
    type?: string
    text?: string
  }

  /**
   * A Props
   */
  const props = defineProps<{
    'attributes': AAttributes
  }>()

  /**
   * Default A Attributes
   */
  const defaultAttributes: Partial<AAttributes> = {
    download: undefined,
    href: undefined,
    id: undefined,
    referrerpolicy: undefined,
    rel: undefined,
    tabindex: undefined,
    target: undefined,
    type: undefined,
    text: undefined,
  }

  /**
   * A Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <a
    class="a"
    :download="attributes.download"
    :href="attributes.href"
    :id="attributes.id"
    :referrerpolicy="attributes.referrerpolicy"
    :rel="attributes.rel"
    :tabindex="attributes.tabindex"
    :target="attributes.target"
    :type="attributes.target"
    v-html="attributes.text"
  ></a>
</template>

<style scoped>
  .a {
    color: rgb(37, 37, 37);
    text-decoration: none;
  }
</style>