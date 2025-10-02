<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Textarea Interface
   */
  interface TextareaAttributes {
    autofocus?: boolean
    cols?: number
    disabled?: boolean
    id?: string
    maxlength?: number
    name?: string
    placeholder?: string
    readonly?: boolean
    required?: boolean
    rows?: number
    tabindex?: number | string
  }

  /**
   * Textarea Props
   */
  const props = defineProps<{
    'attributes': TextareaAttributes
  }>()

  /**
   * Default Textarea Attributes
   */
  const defaultAttributes: Partial<TextareaAttributes> = {
    autofocus: false,
    cols: 50,
    disabled: false,
    id: undefined,
    maxlength: undefined,
    name: undefined,
    placeholder: undefined,
    readonly: false,
    required: true,
    rows: 5,
    tabindex: undefined,
  }

  /**
   * Textarea Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Textarea Define Model
   */
  const modelValue = defineModel<string>();
</script>

<template>
  <textarea
    class="textarea"
    :autofocus="attributes.autofocus"
    :cols="attributes.cols"
    :disabled="attributes.disabled"
    :id="attributes.id"
    :maxlength="attributes.maxlength"
    :name="attributes.name"
    :placeholder="attributes.placeholder"
    :readonly="attributes.readonly"
    :required="attributes.required"
    :rows="attributes.rows"
    :tabindex="attributes.tabindex"
    v-model="modelValue"
  >
  </textarea>
</template>

<style scoped>
  .textarea {
    box-sizing: content-box;
    padding: 5px 5px;
    font-size: 16px;
    border-radius: 3px;
    border: solid rgb(37, 37, 37) 2px;
    background-color: rgb(255, 255, 255);
  }
</style>