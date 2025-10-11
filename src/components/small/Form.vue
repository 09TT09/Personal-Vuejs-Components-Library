<script setup lang="ts">
  import { computed } from 'vue'

  /**
   * Form Interface
   */
  interface FormAttributes {
    acceptCharset?: string
    action?: string
    autocomplete?: 'on' | 'off'
    enctype?: 'application/x-www-form-urlencoded' | 'multipart/form-data' | 'text/plain'
    id?: string
    method?: 'get' | 'post' | 'dialog'
    name?: string
    novalidate?: boolean
    role?: string
    target?: '_self' | '_blank' | '_parent' | '_top'
  }

  /**
   * Form Props
   */
  const props = defineProps<{
    attributes?: FormAttributes
  }>()

  /**
   * Default Form Attributes
   */
  const defaultAttributes: Partial<FormAttributes> = {
    acceptCharset: undefined,
    action: undefined,
    autocomplete: 'on',
    enctype: 'application/x-www-form-urlencoded',
    id: undefined,
    method: 'post',
    name: undefined,
    novalidate: false,
    role: 'form',
    target: '_self',
  }

  /**
   * Form Compute Attributes
   */
  const attributes = computed(() => ({
    ...defaultAttributes,
    ...props.attributes,
  }))

  /**
   * Form Submit Emit
   */
  const emit = defineEmits<{
    (e: 'submit', event: SubmitEvent): void
  }>()

  /**
   * Form Handle Submit
   */
  function handleSubmit(event: SubmitEvent) {
    event.preventDefault()
    emit('submit', event)
  }
</script>

<template>
  <form
    class="form"
    :acceptCharset="attributes.acceptCharset"
    :action="attributes.action"
    :autocomplete="attributes.autocomplete"
    :enctype="attributes.enctype"
    :id="attributes.id"
    :method="attributes.method"
    :name="attributes.name"
    :novalidate="attributes.novalidate"
    :role="attributes.role"
    :target="attributes.target"
    @submit="handleSubmit"
  >
    <slot></slot>
  </form>
</template>

<style scoped>
  .form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
</style>
