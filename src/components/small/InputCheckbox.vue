<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * InputCheckbox Interface
   */
  interface InputCheckboxAttributes {
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
   * InputCheckbox Props
   */
  const props = defineProps<{
    'attributes': InputCheckboxAttributes
  }>()

  /**
   * Default InputCheckbox Attributes
   */
  const defaultAttributes: Partial<InputCheckboxAttributes> = {
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
   * InputCheckbox Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))


  /**
   * InputCheckbox Click Emit
   */
  const emit = defineEmits<{
    (e: 'change', value: boolean): void
  }>()

  /**
   * InputCheckbox Handle Click
   * 
   * @param event 
   */
  function handleChange(event: Event) {
    const target = event.target as HTMLInputElement
    emit('change', target.checked)
  }

  /**
   * InputCheckbox Define Model
   */
  const modelValue = defineModel<Boolean>();
</script>

<template>
  <input
    class="checkbox"
    type="checkbox"
    :autofocus="attributes.autofocus"
    :checked="attributes.checked"
    :disabled="attributes.disabled"
    :id="attributes.id"
    :name="attributes.name"
    :tabindex="attributes.tabindex"
    :value="attributes.value"
    v-model="modelValue"
    @change="handleChange"
  />
</template>

<style scoped>
  input[type=checkbox] {
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
  }

  .checkbox {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 25px;
    width: 25px;
    border: solid rgb(37, 37, 37) 2px;
    border-radius: 3px;
    background-color: rgb(255, 255, 255);
    cursor: pointer;
  }

  .checkbox:checked {
    background-color: rgb(94, 255, 0);
    &:before {
      font-size: 16px;
      content: '✔';
      color: rgb(37, 37, 37);
    }
  }
</style>