<template>
  <main id="container">
    <section id="whatsapp_number">
      <form action="" @submit="submitForm($event)" id="form">
        <h1 id="title">WhatsApp Number!</h1>
        <div class="input-box">
          <div class="input-field">
            <i class="fa-brands fa-whatsapp"></i>
            <input
              type="text"
              v-maska
              data-maska="(##) #####-####"
              v-model="input_number"
              placeholder="Digite o número"
            />
            <span><i class="flag-icon flag-icon-br"></i></span>
          </div>
        </div>
        <input
          type="submit"
          @click="numberClick"
          id="generate"
          value="Gerar Link"
        />
      </form>
      <div v-show="viewNumber">
        <div id="result">
          <a class="value" v-bind:href="api + number" target="_blank">
            {{ api + number }}
            <i class="fa-sharp fa-solid fa-arrow-up-right-from-square"></i>
          </a>
        </div>
      </div>
    </section>
  </main>
</template>
<script setup>
import { vMaska } from "maska";
</script>
<script>
export default {
  name: "whatsAppNumber",

  data() {
    return {
      number: "",
      api: "https://api.whatsapp.com/send?phone=55",
      viewNumber: "",
      input_number: "",
    };
  },
  methods: {
    submitForm(e) {
      e.preventDefault();
      this.number = this.input_number.replace(/\D/g, "");
    },
    numberClick() {
      this.viewNumber = true;
    },
  },
};
</script>
