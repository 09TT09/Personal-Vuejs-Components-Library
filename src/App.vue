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
  import Ol from "./components/small/Ol.vue";
  import Select from "@/components/small/Select.vue";
  import Label from "@/components/small/Label.vue";
  import P from "@/components/small/P.vue";
  import H from "@/components/small/H.vue";
  import Img from "@/components/small/Img.vue";
  import Div from "@/components/small/Div.vue";
  import Span from "@/components/small/Span.vue";
  import Form from "@/components/small/Form.vue";
  import Progress from "@/components/small/Progress.vue";
  import Meter from "@/components/small/Meter.vue";
  import Output from "@/components/small/Output.vue";
  import Header from "@/components/small/Header.vue";
  import Footer from "@/components/small/Footer.vue";
  import Section from "@/components/small/Section.vue";
  import Article from "@/components/small/Article.vue";
  import Nav from "@/components/small/Nav.vue";
  import Video from "@/components/small/Video.vue";
  import Details from "@/components/small/Details.vue";

  import ImageTest1 from "@/../public/images/image-test-1.png";

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
    name: '',
    progress: '75',
    meter: '25',
    output: '10',
  });

  const elements = {
    "button": {
      text: "Button",
    },
    "a": {
      href: "/",
      target: "_blank" as const,
      html: "Link",
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
    "ol": {
      id: "ol",
      li: [
        {html: "<b>Elem 1</b>", id: "li-1"},
        {html: "<i>Elem 2</i>", id: "li-2"},
      ]
    },
    "select": {
      name: "select",
      options: [
        {html: "Select 1", value: "Option 1", disabled: true},
        {
          label: "Parameters",
          options: [
            {html: "Select 2", value: "Option 2", selected: true},
            {html: "Select 3", value: "Option 3"},
          ]
        }
      ]
    },
    "label": {
      html: "Label input text",
      for: "inputNumber"
    },
    "p": {
      html: "Paragraph",
    },
    "h1": { level: "h1" as const, html: "H1" },
    "h2": { level: "h2" as const, html: "H2" },
    "h3": { level: "h3" as const, html: "H3" },
    "h4": { level: "h4" as const, html: "H4" },
    "h5": { level: "h5" as const, html: "H5" },
    "h6": { level: "h6" as const, html: "H6" },
    "img": {
      src: ImageTest1,
      width: 250,
      height: 216,
    },
    "form": {
      id: 'upload',
      method: 'post' as const,
      enctype: 'multipart/form-data' as const,
      acceptCharset: 'UTF-8'
    }
  }

  function onButtonClick(event: MouseEvent) {
    form['button'] += 1
  }

  function onSubmit(event: SubmitEvent) {
    console.log("form submitted")
  }
</script>

<template>
  <section class="main">
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
        <Ol :attributes="elements['ol']" />
      </div>
      <div>
        <Select v-model="form['select']" :attributes="elements['select']" />
        {{ form['select'] }}
      </div>
      <div>
        <Label :attributes="elements['label']" />
      </div>
      <div>
        <P :attributes="elements['p']" />
      </div>
      <div>
        <H :attributes="elements['h1']" />
        <H :attributes="elements['h2']" />
        <H :attributes="elements['h3']" />
        <H :attributes="elements['h4']" />
        <H :attributes="elements['h5']" />
        <H :attributes="elements['h6']" />
      </div>
      <div>
        <Img :attributes="elements['img']" />
      </div>
      <Div>
        <Span :attributes="{ html: 'span' }" />
        <Div><P :attributes="elements['p']" /></Div>
      </Div>
      <Div>
        <Form :attributes="elements['form']" @submit="onSubmit">
          <InputText v-model="form.name" :attributes="{ name: 'name', placeholder: 'Your name' }" />
          <Button :attributes="{ text: 'Send', type: 'submit' }" />
        </Form>
      </Div>
      <Div>
        <Progress :attributes="{ id: 'progress', max: 100 }" v-model="form.progress" />
        {{ form.progress }} %
        <InputText :attributes="{ type: 'number' as const, name: 'progress-number', max: 100 }" v-model="form.progress" />
      </Div>
      <Div>
        <Meter v-model="form.meter" :attributes="{ id: 'cpu', min: 0, max: 100, low: 30, high: 80, optimum: 50 }" />
        {{ form.meter }} %
        <InputText :attributes="{ type: 'number' as const, name: 'meter-number', max: 100 }" v-model="form.meter" />
      </Div>
      <Div>
        <Output v-model="form.output" />
      </Div>
      <Div>
        <Header>
          <P :attributes="{ html: 'Header' }"></P>
        </Header>
      </Div>
      <Div>
        <Footer>
          <P :attributes="{ html: 'Footer' }"></P>
        </Footer>
      </Div>
      <Div>
        <Section>
          <P :attributes="{ html: 'Section' }"></P>
        </Section>
      </Div>
      <Div>
        <Article>
          <P :attributes="{ html: 'Article' }"></P>
        </Article>
      </Div>
      <Div>
        <Nav>
          <P :attributes="{ html: 'Nav' }"></P>
        </Nav>
      </Div>
      <Div>
        <Video :attributes="{
          width: 640,
          height: 360,
          sources: [
            { src: '...', type: 'video/mp4' }
          ]
        }" />
      </Div>
      <Div>
        <Details :attributes="{ summary: { text: 'Summary' } }">
          <P :attributes="{ html: 'details' }"></P>
        </Details>
      </Div>
    </div>
  </section>
</template>

<style scoped>
  h2 {
    margin-top: 0;
    text-align: center;
  }

  .main {
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
