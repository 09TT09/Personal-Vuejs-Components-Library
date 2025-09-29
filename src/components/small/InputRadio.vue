<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * InputRadio Interface
   */
  interface InputRadioAttributes {
    autofocus?: boolean
    checked?: boolean
    disabled?: boolean
    id?: string
    name?: string
    required?: boolean
    tabindex?: number | string
    value?: string
  }

  /**
   * InputRadio Props
   */
  const props = defineProps<{
    'attributes': InputRadioAttributes
  }>()

  /**
   * Default InputRadio Attributes
   */
  const defaultAttributes: Partial<InputRadioAttributes> = {
    autofocus: false,
    checked: false,
    disabled: false,
    id: undefined,
    name: undefined,
    required: true,
    tabindex: undefined,
    value: undefined,
  }

  /**
   * InputRadio Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * InputRadio Define Model
   */
  const modelValue = defineModel<String>();
</script>

<template>
  <input
    class="inputradio"
    type="radio"
    :autofocus="attributes.autofocus"
    :checked="attributes.checked"
    :disabled="attributes.disabled"
    :id="attributes.id"
    :name="attributes.name"
    :tabindex="attributes.tabindex"
    :value="attributes.value"
    v-model="modelValue"
  />
</template>

<style scoped>
  input[type=radio] {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
  }

  .inputradio {
    position: relative;
    height: 20px;
    width: 20px;
    border: solid rgb(37, 37, 37) 2px;
    border-radius: 100%;
    background-color: rgb(255, 255, 255);
    cursor: pointer;
  }

  .inputradio:checked {
    &:before {
      position: absolute;
      top: calc(50% - 6px);
      left: calc(50% - 6px);
      display: block;
      content: '';
      width: 12px;
      height: 12px;
      border-radius: 100%;
      background-color: rgb(0, 160, 8);
    }
  }
</style>