<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Meter Interface
   */
  interface MeterAttributes {
    high?: number | string
    id?: string
    low?: number | string
    max?: number | string
    min?: number | string
    optimum?: number | string
    value?: number | string
  }

  /**
   * Meter Props
   */
  const props = defineProps<{
    'attributes': MeterAttributes
  }>()

  /**
   * Default Meter Attributes
   */
  const defaultAttributes: Partial<MeterAttributes> = {
    high: undefined,
    id: undefined,
    low: undefined,
    max: 100,
    min: 0,
    optimum: undefined,
    value: undefined,
  }

  /**
   * Meter Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Meter Define Model
   */
  const modelValue = defineModel<number | string>()

  /**
   * Calculate percentage of the meter
   */
  function meterPercentage(value?: string | number, min?: string | number, max?: string | number): string {
    const v = Number(value)
    const minV = Number(min)
    const maxV = Number(max)

    if (isNaN(v) || isNaN(minV) || isNaN(maxV) || maxV <= minV) return '0%'

    const percent = Math.min(100, Math.max(0, ((v - minV) / (maxV - minV)) * 100))
    return `${percent}%`
  }
</script>

<template>
  <meter
    class="meter"
    :high="attributes.high"
    :id="attributes.id"
    :low="attributes.low"
    :max="attributes.max"
    :min="attributes.min"
    :optimum="attributes.optimum"
    :value="modelValue ?? attributes.value"
  >
    {{ meterPercentage(modelValue ?? attributes.value, attributes.min, attributes.max) }}
  </meter>
</template>

<style scoped>
  .meter {
    width: 200px;
  }
</style>
