<template>
  <div class="text-center" id="app">
    <div class="container align-middle">
      <div class="jumbotron">
        <h1 class="display-3">Easy Translator</h1>
        <p
          class="lead"
        >This is a lightweight translator where you can translate English text to any language.
          <br>Built with Vue.js and Yandex Translate API.
        </p>
        <hr class="my-4">
        <div class="row">
          <div class="col col-md-5">
            <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
          </div>
          <div class="col col-md-7">
            <div v-if="translatedText.length > 1" class="card text-white bg-primary mb-3">
              <div class="card-header">Translated text:</div>
              <div class="card-body">
                <p class="card-text">
                  <TranslateOutput v-text="translatedText"></TranslateOutput>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import TranslateOutput from "./components/TranslateOutput";

export default {
  name: "App",
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText: ""
      //languageName: ""
    };
  },
  methods: {
    translateText: function(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190116T152956Z.28567260c57ba875.f2516dec227514f0723cfb8df26f76695a3acc09&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          // get body data
          this.translatedText = response.body.text[0];
        });
    }
  }
};
</script>

<style>
#app {
  position: relative;
  width: 100%;
  height: 100%;
}
</style>
