<template>
    <form @submit.prevent="TranslateIt" class="well">
        <textarea v-model="searchText" cols="30" rows="5" class="form-control"
            placeholder="Çevirmek istediğiniz kelime/cümle yazınız."></textarea>
        <select class="form-control" v-model="translateTo">
            <option v-bind:key="y" v-for="(x,y) in languages" :value="y">{{ x }}</option>
        </select>
        <br />
        <div class="text-left">
            <strong>Çevirilecek Dil : </strong> <span v-text="languages[translateTo]"></span>
        </div>
        <br />
        <button type="submit" class="btn btn-primary btn-block">Çevir Gelsin!</button>
    </form>
</template>

<script>
    import axios from "axios";
    export default {
        data() {
            return {
                searchText: "",
                languages: [],
                translateTo: ""
            };
        },
        methods: {
            TranslateIt() {
  
                let baseurl = "https://translate.yandex.net/api/v1.5/tr.json/translate";
                let key =
                    "key=trnsl.1.1.20191101T122016Z.d309aa15307d111a.bbc09a62db05a128902be1154370f270289d4294";
                let text = "text=" + this.searchText;
                let lang = "lang=" + this.translateTo;

                let requestUrl = baseurl + "?" + key + "&" + text + "&" + lang;

                axios
                    .get(requestUrl)
                    .then(res => {
                        console.log(res.data.text[0]);
                        this.$emit("OnTranslated",res.data.text[0]);
                    })
                    .catch(err => {
                        console.log(err);
                    });
            }
        },
        created() {
            let baseurl = "https://translate.yandex.net/api/v1.5/tr.json/getLangs";
            let key =
                "key=trnsl.1.1.20191101T122016Z.d309aa15307d111a.bbc09a62db05a128902be1154370f270289d4294";
            let ui = "ui=tr";

            let requestUrl = baseurl + "?" + key + "&" + ui;

            axios
                .get(requestUrl)
                .then(res => {
                    this.languages = res.data.langs;
                })
                .catch(err => {
                    console.log(err);
                });
        }
    };
</script>
<style></style>