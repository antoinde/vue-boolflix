<template>
    <header class="row">
        
        <div class="col-12 d-flex justify-content-center">
            <div class="search-area">
                <span>Search here: </span>
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
</style>
  