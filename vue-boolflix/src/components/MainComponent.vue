<template>
    <main class="row mt-4">
        <div class="col-12">
            MAIN
        </div>
        <div class="col-12">
            <ul>
                <li v-for="film in sentFilms" :key="film.id">
                    <h6>{{ film.title }}</h6>
                    <p>
                        {{ film.original_title }} <br>
                        {{ film.original_language }} <br>
                        {{ film.vote_average }} <br>
                    </p>
                </li>
            </ul>
        </div>
    </main>
</template>
  
<script>
  
  
export default {
    name: 'MainComponent',
    props: {
        sentFilms: Array
    }
    
}
</script>
  
<style lang="scss" scoped>
li {
    list-style-type: none;
    border: 1px solid black;
    padding: 15px;
}
  
</style>
  