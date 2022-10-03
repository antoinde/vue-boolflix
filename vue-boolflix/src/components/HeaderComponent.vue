<template>
    <header class="row">
        <div class="col-6 d-flex logo">
            <img class="logo" src="@/assets/img/Netflix_logo.svg.png" alt="Logo Netflix">
        </div>
        <div class="col-6 d-flex justify-content-end">
            <div class="search-area">
                <span>Cerca qui: </span>
                <input type="text"  v-model="textToSearch" @keyup.enter="sendRequest()">
                <button @click="sendRequest()" >Cerca!</button>
            </div>
        </div>
    </header>
</template>
  
<script>

export default {
    name: 'HeaderComponent',
    data(){
        return {
            textToSearch: '',
        }
    },
    methods: {
        sendRequest(){

            this.$emit("search", this.textToSearch);
        }
    }

}
</script>
  
<style lang="scss" scoped>
.search-area{
    margin-top: 30px;
}
input{
    margin: 0 10px;
}
.logo{
    height: 50px;
    margin-top: 10px;
}
</style>
  