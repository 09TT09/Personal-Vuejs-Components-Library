<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Progress Interface
   */
  interface ProgressAttributes {
    id?: string
    max?: number | string
    value?: number | string
  }

  /**
   * Progress Props
   */
  const props = defineProps<{
    'attributes': ProgressAttributes
  }>()

  /**
   * Default Progress Attributes
   */
  const defaultAttributes: Partial<ProgressAttributes> = {
    id: undefined,
    max: 100,
    value: 50,
  }

  /**
   * Progress Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))


  /**
   * Progress Define Model
   */
  const modelValue = defineModel<string | number>();

  /**
   * Calculate the progress
   */
  function progressCalculate(value?: string | number, max?: string | number): string {
    const intValue = Number(value);
    const intMax = Number(max);

    if (!intMax || isNaN(intValue) || isNaN(intMax)) return '0%';

    const percent = Math.min(100, Math.max(0, (intValue / intMax) * 100));
    return `${percent}%`;
  }
</script>

<template>
  <progress
    class="progress"
    :id="attributes.id"
    :max="attributes.max"
    :value="modelValue ?? attributes.value"
  >
    {{ progressCalculate((modelValue! ?? attributes.value) , attributes.max!) }}
  </progress>
</template>

<style scoped>
  .progress {
    width: 200px;
    height: 12px;
    -webkit-appearance: none;
    appearance: none;
  }

  .progress::-webkit-progress-bar {
    border-radius: 3px;
    background-color: #ffffff;
  }

  .progress::-webkit-progress-value, .progress::-moz-progress-bar {
    background-color: rgb(0, 160, 8);
    border-radius: 3px 0 0 3px;
    transition: width 0.25s ease;
  }

  .progress[value="100"]::-webkit-progress-value, .progress[value="100"]::-moz-progress-bar {
    border-radius: 3px;
  }
</style>