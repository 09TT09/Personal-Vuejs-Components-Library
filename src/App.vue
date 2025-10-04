<script setup lang="ts">
  import "@/../public/styles/main.css"
  import { reactive } from "vue";
  import Button from '@/components/small/Button.vue';
  import A from "@/components/small/A.vue";
  import InputText from "@/components/small/InputText.vue";
  import InputCheckbox from "@/components/small/InputCheckbox.vue";
  import InputRadio from "@/components/small/InputRadio.vue";
  import Textarea from "@/components/small/Textarea.vue";
  import Ul from "@/components/small/Ul.vue";
  import Select from "@/components/small/Select.vue";

  const form = reactive({
    button: 0,
    inputText: 'Input Text',
    inputNumber: '12345678',
    inputPassword: 'Password',
    inputEmail: 'email@test.com',
    inputTel: '0611111111',
    inputUrl: 'https://www.google.com',
    inputCheckbox: false,
    inputRadio: '-',
    textarea: 'This is a text',
    select: 'Option 2',
  });

  const elements = {
    "button": {
      text: "Button",
    },
    "a": {
      href: "/",
      target: "_blank" as const,
      text: "Link",
    },
    "inputText": {
      type: "text" as const,
      name: "inputText"
    },
    "inputNumber": {
      type: "number" as const,
      name: "inputNumber"
    },
    "inputPassword": {
      type: "password" as const,
      name: "inputPassword"
    },
    "inputEmail": {
      type: "email" as const,
      name: "inputEmail",
    },
    "inputTel": {
      type: "tel" as const,
      name: "inputTel",
    },
    "inputUrl": {
      type: "url" as const,
      name: "inputUrl",
    },
    "inputCheckbox": {
      name: "inputCheckbox",
    },
    "inputRadio": {
      "1": {name: "inputRadio", value: "1000"},
      "2": {name: "inputRadio", value: "2000"}
    },
    "textarea": {
      name: "textarea"
    },
    "ul": {
      id: "ul",
      li: [
        {html: "<b>Elem 1</b>", id: "li-1"},
        {html: "<i>Elem 2</i>", id: "li-2"},
      ]
    },
    "select": {
      name: "select",
      option: [
        {html: "Select 1", value: "Option 1", disabled: true},
        {html: "Select 2", value: "Option 2", selected: true},
        {html: "Select 3", value: "Option 3"},
      ]
    }
  }

  function onButtonClick(event: MouseEvent) {
    form['button'] += 1
  } 
</script>

<template>
  <section>
    <h2>Small components</h2>
    <div class="small-components-box">
      <div style="display: flex;  align-items:center; gap: 30px;">
        <Button :attributes="elements['button']" @click="onButtonClick" />
        {{ form['button'] }}
      </div>
      <A :attributes="elements['a']" />
      <div>
        <InputText v-model="form['inputText']" :attributes="elements['inputText']" />
        {{  form['inputText'] }}
      </div>
      <div>
        <InputText v-model="form['inputNumber']" :attributes="elements['inputNumber']" />
        {{  form['inputNumber'] }}
      </div>
      <div>
        <InputText v-model="form['inputPassword']" :attributes="elements['inputPassword']" />
        {{  form['inputPassword'] }}
      </div>
      <div>
        <InputText v-model="form['inputEmail']" :attributes="elements['inputEmail']" />
        {{  form['inputEmail'] }}
      </div>
      <div>
        <InputText v-model="form['inputTel']" :attributes="elements['inputTel']" />
        {{  form['inputTel'] }}
      </div>
      <div>
        <InputText v-model="form['inputUrl']" :attributes="elements['inputUrl']" />
        {{  form['inputUrl'] }}
      </div>
      <div style="display: flex;  align-items:center; gap: 30px;">
        <InputCheckbox v-model="form['inputCheckbox']" :attributes="elements['inputCheckbox']" />
        {{ form['inputCheckbox'] }}
      </div>
      <div>
        <InputRadio v-model="form['inputRadio']" :attributes="elements['inputRadio']['1']" />
        <InputRadio v-model="form['inputRadio']" :attributes="elements['inputRadio']['2']" />
        {{ form['inputRadio'] }}
      </div>
      <div>
        <Textarea v-model="form['textarea']" :attributes="elements['textarea']" />
        {{ form['textarea'] }}
      </div>
      <div>
        <Ul :attributes="elements['ul']" />
      </div>
      <div>
        <Select v-model="form['select']" :attributes="elements['select']" />
        {{ form['select'] }}
      </div>
    </div>
  </section>
</template>

<style scoped>
  h2 {
    margin-top: 0;
    text-align: center;
  }

  section {
    padding: 20px;
    border-radius: 3px;
    border: solid rgb(37, 37, 37) 1px;
  }

  .small-components-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }
</style>
