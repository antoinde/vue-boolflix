<template>
    <header>
        <div class="row">
            <div class="col-4 d-flex logo">
                <img class="logo" src="@/assets/img/Netflix_logo.svg.png" alt="Logo Netflix">
            </div>
            <div class="col-4 d-flex justify-content-end">
                <div class="search-area d-flex align-items-center">
                    <span>Cerca qui: </span>
                    <input type="text"  v-model="textToSearch" @keyup.enter="sendRequest()">
                    <button @click="sendRequest()" >Cerca!</button>
                </div>
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
header {
    padding: 20px 0px;
    position:fixed;
    top: 0px;
    z-index: 999;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.667);
}
.search-area{
    // margin-top: 30px;
}
input{
    margin: 0 10px;
}
.logo{
    height: 50px;
    // margin-top: 10px;
}

</style>
  