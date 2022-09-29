<template>
    <header class="row">
        
        <div class="col-12">
            <div>HEADER</div>
            <input type="text"  v-model="textToSearch" @keyup.enter="sendRequest()">
            <div>{{textToSearch}}</div>
            <button @click="sendRequest()" >Cerca!</button>
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

</style>
  