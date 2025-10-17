<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Img Interface
   */
  interface ImgAttributes {
    alt?: string
    crossorigin?: "anonymous" | "use-credentials"
    decoding?: "sync" | "async" | "auto"
    elementtiming?: string
    fetchpriority?: "high" | "low" | "auto"
    height?: number | string
    id?: string
    ismap?: boolean
    loading?: "eager" | "lazy"
    referrerpolicy?: "no-referrer" | "no-referrer-when-downgrade" | "origin" | "origin-when-cross-origin" | "same-origin" | "strict-origin" | "strict-origin-when-cross-origin" | "unsafe-url"
    sizes?: string
    src?: string
    srcset?: string
    width?: number | string
    usemap?: string
  }

  /**
   * Img Props
   */
  const props = defineProps<{
    attributes: ImgAttributes
  }>()

  /**
   * Default Img Attributes
   */
  const defaultAttributes: Partial<ImgAttributes> = {
    alt: undefined,
    crossorigin: undefined,
    decoding: undefined,
    elementtiming: undefined,
    fetchpriority: undefined,
    height: undefined,
    id: undefined,
    ismap: undefined,
    loading: undefined,
    referrerpolicy: undefined,
    sizes: undefined,
    src: undefined,
    srcset: undefined,
    width: undefined,
    usemap: undefined,
  }

  /**
   * Img Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>

  <img
    class="img"
    :alt="attributes.alt"
    :crossorigin="attributes.crossorigin"
    :decoding="attributes.decoding"
    :elementtiming="attributes.elementtiming"
    :fetchpriority="attributes.fetchpriority"
    :height="attributes.height"
    :id="attributes.id"
    :ismap="attributes.ismap"
    :loading="attributes.loading"
    :referrerpolicy="attributes.referrerpolicy"
    :sizes="attributes.sizes"
    :src="attributes.src"
    :srcset="attributes.srcset"
    :width="attributes.width"
    :usemap="attributes.usemap"
  />
</template>

<style scoped>
</style>