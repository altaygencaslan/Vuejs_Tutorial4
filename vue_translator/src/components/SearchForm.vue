<template>
    <form @submit.prevent="TranslateIt" class="well">
        <textarea v-model="searchText" cols="30" rows="5" class="form-control"
            placeholder="Çevirmek istediğiniz kelime/cümle yazınız."></textarea>
        <select class="form-control">
            <option></option>
        </select>
        <br>
        <div class="text-left">
            <strong>Tespit Edilen Dil : </strong>
        </div>
        <br>
        <button type="submit" class="btn btn-primary btn-block">Çevir Gelsin!</button>
    </form>
</template>
<script>
    import axios from "axios"
    export default {
        data() {
            return {
                searchText: ""
            }
        },
        methods: {
            TranslateIt() {
                let baseurl = "https://translate.yandex.net/api/v1.5/tr.json/translate";
                let key = "key=trnsl.1.1.20191101T122016Z.d309aa15307d111a.bbc09a62db05a128902be1154370f270289d4294";
                let text = "text=" + this.searchText;
                let lang = "lang=en";

                let requestUrl = baseurl + "?" + key + "&" + text + "&" + lang;

                axios.get(requestUrl)
                    .then(res => {
                        console.log(res.data.text)
                    }).catch(err => {
                        console.log(err)
                    });
            }
        }
    }
</script>
<style></style>