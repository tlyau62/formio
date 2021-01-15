<template>
  <b-container class="home">
    <div class="my-3">
      <h4>Form builder</h4>
      <form-builder
        :form="form"
        :options="{}"
        @change="updateScheme"
      ></form-builder>
    </div>

    <div class="my-3">
      <h4>Form renderer</h4>
      <formio
        :form="form"
        :submission="submission"
        options=""
        @submit="submit"
        :key="key"
      />
    </div>
  </b-container>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import { Form, FormBuilder } from "vue-formio";
import FormioFormBuilder from "formiojs/FormBuilder";

/**
 * There is no way to use a event other than 'change' to get the scheme
 * Test method:
 * onChange(evt) {
 *   debug;
 *   console.log(evt);
 * },
 */

export default {
  name: "Home",
  components: {
    HelloWorld,
    Formio: Form,
    FormBuilder,
  },
  data() {
    return {
      form: { display: "form" },
      submission: {},
      key: 0,
    };
  },
  methods: {
    updateScheme(evt) {
      if (evt.display && evt.components) {
        console.log(evt);
        this.form = evt;
        this.key++;
      }
    },
    submit(evt) {
      console.log(evt);
    },
  },
};
</script>
