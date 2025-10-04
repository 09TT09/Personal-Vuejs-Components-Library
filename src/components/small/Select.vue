<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Option Interface
   */
  interface OptionAttributes {
    disabled?: boolean
    html?: string
    id?: string
    label?: string
    selected?: boolean
    value?: string
  }

  /**
   * Select Interface
   */
  interface SelectAttributes {
    autofocus?: boolean
    disabled?: boolean
    id?: string
    multiple?: boolean
    name?: string
    required?: boolean
    tabindex?: number | string
    size?: number
    option?: OptionAttributes[]
  }

  /**
   * Select Props
   */
  const props = defineProps<{
    'attributes': SelectAttributes
  }>()

  /**
   * Default Select Attributes
   */
  const defaultAttributes: Partial<SelectAttributes> = {
    autofocus: false,
    disabled: false,
    id: undefined,
    multiple: undefined,
    name: undefined,
    required: true,
    tabindex: undefined,
    size: undefined,
  }

  /**
   * Select Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Select Define Model
   */
  const modelValue = defineModel<String>();
</script>

<template>
  <select
    class="select"
    :autofocus="attributes.autofocus"
    :disabled="attributes.disabled"
    :id="attributes.id"
    :multiple="attributes.multiple"
    :name="attributes.name"
    :required="attributes.required"
    :tabindex="attributes.tabindex"
    :size="attributes.size"
    v-model="modelValue"
  >
    <option
      v-for="elem in attributes.option"
      :key="elem.id ?? elem.html"
      :disabled="elem.disabled"
      :id="elem.id"
      :label="elem.label"
      :selected="elem.selected"
      :value="elem.value"
      v-html="elem.html"
    >
    </option>
  </select>
</template>

<style scoped>
  .select {
    box-sizing: content-box;
    padding: 5px 10px;
    height: 30px;
    min-width: 180px;
    font-size: 16px;
    border-radius: 3px;
    border: solid rgb(37, 37, 37) 2px;
    background-color: rgb(255, 255, 255);
  }
</style>