<template>
  <div id="translateForm">
    <div class="card">
      <h3 class="card-header">Translate</h3>
      <div class="card-body">
        <form class="well" v-on:submit="formSubmit">
          <div class="form-group">
            <textarea
              rows="4"
              cols="50"
              v-model="textToTranslate"
              placeholder="Enter your English text"
            >
At w3schools.com you will learn how to make a website. We offer free tutorials in all web development technologies.
</textarea>
          </div>
          <div class="form-group">
            <label for="languageSelect">Select the Language:</label>
            <select class="form-control" id="languageSelect" v-model="language">
              <option value="sr">Serbian</option>
              <option value="ru">Russian</option>
              <option value="es">Spanish</option>
              <option value="fr">French</option>
              <option value="it">Italian</option>
              <option value="de">German</option>
              <option value="da">Danish</option>
              <option value="ar">Arabic</option>
              <option value="hu">Hungarian</option>
              <option value="da">Dutch</option>
              <option value="ja">Japanese</option>
              <option value="az">Azerbaijan</option>
            </select>
          </div>
          <input class="btn btn-primary" type="submit" value="Translate">
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "translateForm",
  data() {
    return {
      textToTranslate: "",
      language: ""
    };
  },
  created() {
    this.language = "ru";
  },
  methods: {
    formSubmit(e) {
      this.$emit("formSubmit", this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
};
</script>

<style>
</style>
