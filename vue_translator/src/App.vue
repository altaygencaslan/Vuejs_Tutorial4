<template>
  <div class="container">
    <h1 class="text-center">Vue-Translator</h1>
    <h5 class="text-center">Vue.js ile Translator</h5>
    <br>

    <div class="row">
      <div class="col-md-12 text-center">
        <SearchForm @OnTranslated="Translated($event)" />
        <h3 class="text-success text-center"></h3>
        <History />  
      </div>
    </div>
  </div>
</template>

<script>
  import SearchForm from "./components/SearchForm"
  import History from "./components/History"
  export default {
    components: {
      SearchForm, // SearchForm : SearchForm
      History // History : History
    },
    methods:{
      Translated(message){
        alert(message);
      }
    }
  }
</script>

<style>
body{
  background-color: #dedede;
}
</style>