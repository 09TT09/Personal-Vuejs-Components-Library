<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * InputText Interfaces
   */
  interface GlobalAttributes {
    autocomplete?: string
    autofocus?: boolean
    disabled?: boolean
    id?: string
    name: string
    placeholder?: string
    readonly?: boolean
    required?: boolean
    tabindex?: number | string
  }

  interface TextAttributes extends GlobalAttributes {
    maxlength?: number | string
    minlength?: number | string
    pattern?: string
    type: "text" | "password" | "email" | "url" | "tel"
  }

  interface EmailAttributes extends GlobalAttributes {
    multiple?: boolean
  }

  interface NumberAttributes extends GlobalAttributes {
    max?: number | string
    min?: number | string
    step?: number | string
    type: "number"
  }

  /**
   * Attribute Types Union
   */
  type InputTextAttributes = TextAttributes | EmailAttributes | NumberAttributes

  /**
   * InputText Props
   */
  const props = defineProps<{
    'attributes': InputTextAttributes
  }>()

  /**
   * Default InputText Attributes
   */
  const defaultAttributes: Partial<InputTextAttributes> = {
    autocomplete: undefined,
    autofocus: false,
    disabled: false,
    id: undefined,
    name: undefined,
    placeholder: undefined,
    readonly: false,
    required: true,
    tabindex: undefined,
    type: "text",
  }

  /**
   * InputText Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * InputText Define Model
   */
  const modelValue = defineModel<string>();
</script>

<template>
  <input
    class="input_text"
    :autocomplete="attributes.autocomplete"
    :autofocus="attributes.autofocus"
    :disabled="attributes.disabled"
    :id="attributes.id"
    :name="attributes.name"
    :placeholder="attributes.placeholder"
    :readonly="attributes.readonly"
    :required="attributes.required"
    :tabindex="attributes.tabindex"
    :type="attributes.type"
    :maxlength="'maxlength' in attributes ? attributes.maxlength : undefined"
    :minlength="'minlength' in attributes ? attributes.minlength : undefined"
    :pattern="'pattern' in attributes ? attributes.pattern : undefined"
    :max="'max' in attributes ? attributes.max : undefined"
    :min="'min' in attributes ? attributes.min : undefined"
    :step="'step' in attributes ? attributes.step : undefined"
    :multiple="'multiple' in attributes ? attributes.multiple : undefined"
    v-model="modelValue"
  />
</template>

<style scoped>
  .input_text {
    box-sizing: content-box;
    padding: 5px 10px;
    height: 30px;
    min-width: 180px;
    font-size: 16px;
    border-radius: 3px;
    border: solid rgb(37, 37, 37) 2px;
    background-color: rgb(255, 255, 255);
  }

  input[type=number]::-webkit-outer-spin-button,
  input[type=number]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  input[type=number] {
    -moz-appearance: textfield;
  }
</style>