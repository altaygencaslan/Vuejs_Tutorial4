<template>
  <div class="well">
    <h3>Arama Geçmişi</h3>
    <ul class="list-group text-left">
      <li class="list-group-item" v-for="item in historyList" v-bind:key="item">
        <div>
          <strong>{{ item.fromLang }} > {{ item.toLang }}</strong>
        </div>
        <br />
        <div>
          <strong class="text-success" v-text="item.fromText"></strong>
          :
          <span class="text-info" v-text="item.toText"></span>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["historyList"]
};
</script>
<style scoped>
.list-group-item {
    margin-bottom: 5px !important;
}
</style>