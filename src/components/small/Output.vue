<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Output Interface
   */
  interface OutputAttributes {
    for?: string
    form?: string
    html?: string
    id?: string
    name?: string
  }

  /**
   * Output Props
   */
  const props = defineProps<{
    attributes?: OutputAttributes
  }>()

  /**
   * Default Output attributes
   */
  const defaultAttributes: Partial<OutputAttributes> = {
    for: undefined,
    form: undefined,
    html: undefined,
    id: undefined,
    name: undefined,
  }

  /**
   * Output Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Output Define Model
   */
  const modelValue = defineModel<string>()
</script>

<template>
  <output
    class="output"
    :for="attributes.for"
    :form="attributes.form"
    :id="attributes.id"
    :name="attributes.name"
  >
    <template v-if="modelValue">{{ modelValue }}</template>
    <template v-else-if="attributes.html" v-html="attributes.html"></template>
    <slot v-else></slot>
  </output>
</template>

<style scoped>
  .output {
    display: inline-block;
    box-sizing: content-box;
    padding: 5px 15px;
    font-size: 16px;
    border-radius: 3px;
    border: solid rgb(37, 37, 37) 2px;
    background-color: rgb(255, 255, 255);
  }
</style>
