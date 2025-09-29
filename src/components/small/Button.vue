<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Button Interface
   */
  interface ButtonAttributes {
    autofocus?: boolean
    disabled?: boolean
    id?: string
    loading?: boolean
    name?: string
    tabindex?: number | string
    text?: string
    type?: "button" | "submit" | "reset"
    value?: number | string
  }

  /**
   * Button Props
   */
  const props = defineProps<{
    'attributes': ButtonAttributes
  }>()

  /**
   * Default Button Attributes
   */
  const defaultAttributes: Partial<ButtonAttributes> = {
    autofocus: false,
    disabled: false,
    id: undefined,
    loading: false,
    name: undefined,
    tabindex: undefined,
    text: undefined,
    type: "button",
    value: undefined,
  }

  /**
   * Button Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Button Click Emit
   */
  const emit = defineEmits<{
    (e: 'click', event: MouseEvent): void
  }>()

  /**
   * Button Handle Click
   * 
   * @param event 
   */
  function handleClick(event: MouseEvent) {
    if (!props.attributes.disabled && !attributes.value.loading) {
      emit('click', event)
    }
  }
</script>

<template>
  <button
    class="button"
    :autofocus="attributes.autofocus"
    :disabled="attributes.disabled || attributes.loading"
    :id="attributes.id"
    :name="attributes.name"
    :tabindex="attributes.tabindex"
    :type="attributes.type"
    :value="attributes.value"
    @click="handleClick"
  >
    <span v-if="attributes.loading" class="spinner"></span>
    <span v-else v-html="attributes.text"></span>
  </button>
</template>

<style scoped>
  .button {
    display: flex;
    justify-content: center;
    align-items: center;
    min-width: 100px;
    min-height: 40px;
    padding: 10px;
    border: 0;
    border-radius: 3px;
    font-size: 16px;
    color: rgb(255, 255, 255);
    background-color: rgb(37, 37, 37);
    cursor: pointer;
    transition: 0.25s;
  }

  .button:hover {
    background-color: rgb(50, 50, 50);
  }

  .spinner {
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid transparent;
    border-top-color: rgb(255, 255, 255);
    border-left-color: rgb(255, 255, 255);
    border-radius: 50%;
    animation: spin 0.5s linear infinite;
    margin-right: 0.5em;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }
</style>