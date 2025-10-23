<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Video Source Interface
   */
  interface VideoSource {
    src: string
    type?: string
  }

  /**
   * Video Interface
   */
  interface VideoAttributes {
    ariaLabel?: string
    autoplay?: boolean
    controls?: boolean
    crossorigin?: 'anonymous' | 'use-credentials'
    height?: number | string
    id?: string
    loop?: boolean
    muted?: boolean
    playsinline?: boolean
    poster?: string
    preload?: 'none' | 'metadata' | 'auto'
    width?: number | string
    sources?: VideoSource[]
  }

  /**
   * Video Props
   */
  const props = defineProps<{
    attributes: VideoAttributes
  }>()

  /**
   * Default Video Attributes
   */
  const defaultAttributes: Partial<VideoAttributes> = {
    ariaLabel: undefined,
    autoplay: false,
    controls: true,
    crossorigin: undefined,
    height: undefined,
    id: undefined,
    loop: false,
    muted: false,
    playsinline: false,
    poster: undefined,
    preload: 'metadata',
    width: undefined,
    sources: undefined,
  }

  /**
   * Video Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))
</script>

<template>
  <video
    class="video"
    :aria-label="attributes.ariaLabel"
    :autoplay="attributes.autoplay"
    :controls="attributes.controls"
    :crossorigin="attributes.crossorigin"
    :height="attributes.height"
    :id="attributes.id"
    :loop="attributes.loop"
    :muted="attributes.muted"
    :playsinline="attributes.playsinline"
    :poster="attributes.poster"
    :preload="attributes.preload"
    :width="attributes.width"
  >
    <template v-if="attributes.sources && attributes.sources.length">
      <source
        v-for="(source, index) in attributes.sources"
        :key="index"
        :src="source.src"
        :type="source.type"
      />
    </template>
    <slot v-else />
  </video>
</template>

<style scoped>
  .video {
    display: block;
    max-width: 100%;
    border-radius: 6px;
    background-color: #000;
  }
</style>
