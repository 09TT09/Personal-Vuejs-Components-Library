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
   * Optgroup Interface
   */
  interface OptgroupAttributes {
    label: string
    disabled?: boolean
    options: OptionAttributes[]
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
    options?: (OptionAttributes | OptgroupAttributes)[]
  }

  /**
   * Select Props
   */
  const props = defineProps<{
    attributes: SelectAttributes
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
    options: [],
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
  const modelValue = defineModel<string | string[]>();
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
    <template v-for="(item, index) in attributes.options" :key="index">
      <optgroup
        v-if="'options' in item"
        :label="item.label"
        :disabled="item.disabled"
      >
        <option
          v-for="opt in item.options"
          :key="opt.id ?? opt.value ?? opt.html"
          :disabled="opt.disabled"
          :id="opt.id"
          :label="opt.label"
          :selected="opt.selected"
          :value="opt.value"
          v-html="opt.html"
        ></option>
      </optgroup>
      <option
        v-else
        :key="item.id ?? item.value ?? item.html"
        :disabled="item.disabled"
        :id="item.id"
        :label="item.label"
        :selected="item.selected"
        :value="item.value"
        v-html="item.html"
      ></option>
    </template>
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