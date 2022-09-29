<template>
    <main class="row mt-4">
        <div class="col-12">
            MAIN
        </div>
        <div class="col-12">
            <ul>
                <li v-for="film in sentFilms" :key="film.id">
                    <h6> <strong>TITOLO: </strong>  {{ film.title }}</h6>
                    <p> <strong>Titolo originale:</strong>  {{ film.original_title }}</p>
                    <div class="flag"> 
                        <strong>Lingua originale: </strong> 
                        <img :src="getFlag(film.original_language)" :alt="film.original_language" onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'"> 
                    </div>
                    <p> <strong>Voto: </strong> {{ film.vote_average }}</p>
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
    },
    methods: {
        getFlag(initials_flag) {
            console.log(initials_flag);
            if(initials_flag==='en') initials_flag='gb';        
            
            let string = 'https://www.bandiere-mondo.it/data/flags/w702/' + initials_flag + '.webp';
            console.log(string);
            return string;
        },
        
    }
    
}
</script>
  
<style lang="scss" scoped>
li {
    list-style-type: none;
    border: 1px solid black;
    padding: 15px;
}
.flag {
    img {
        width: 30px;
    }
}
.active {
    display: block;
}
.disabled {
    display: none;
}
  
</style>
  