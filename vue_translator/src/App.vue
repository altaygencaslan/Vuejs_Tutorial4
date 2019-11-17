<template>
  <div class="container">
    <h1 class="text-center">Vue-Translator</h1>
    <h5 class="text-center">Vue.js ile Translator</h5>
    <br />

    <div class="row">
      <div class="col-md-12 text-center">
        <SearchForm @OnTranslated="AddHistory($event)" />
        <h3 class="text-success text-center">{{ translatedMessage }}</h3>
        <History :historyList="searchHistory" v-if="searchHistory.length > 0" />
      </div>
    </div>
  </div>
</template>

<script>
import SearchForm from "./components/SearchForm";
import History from "./components/History";
export default {
  components: {
    SearchForm, // SearchForm : SearchForm
    History // History : History
  },
  data() {
    return {
      translatedMessage: "",
      searchHistory: []
    };
  },
  methods: {
    AddHistory(entityClass) {
      this.translatedMessage = entityClass.toText;
      this.searchHistory.push(entityClass);
    }
  }
};
</script>

<style>
body {
  background-color: #dedede;
}
</style>