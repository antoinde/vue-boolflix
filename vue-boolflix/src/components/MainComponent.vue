<template>
    <main class="row mt-4">
        <!-- FILMS -->
        <div class="films">
            <h1> FILM: </h1>
            <ul class="cards">
                <li class="card" v-for="film in sentFilms" :key="film.id">
                    <img :src="getPathImage(film.poster_path)" alt="cover film image" class="image_poster" 
                    onerror="src='//lightwidget.com/wp-content/uploads/local-file-not-found.png'">
                    <h6> <strong>TITOLO: </strong>  {{ film.title }}</h6>
                    <p> <strong>Titolo originale:</strong>  {{ film.original_title }}</p>
                    <div class="flag"> 
                        <strong>Lingua originale: </strong> 
                        <img :src="getFlag(film.original_language)" :alt="film.original_language" 
                        onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'"> 
                        <span> {{film.original_language}} </span>
                    </div>
                    <p> <strong>Voto: </strong> {{ getStar(film.vote_average) }} </p>
                </li>
            </ul>
        </div>

        <!-- SERIES -->
        <div class="series">
            <h1> SERIE TV: </h1>
            <ul class="cards">
                <li class="card" v-for="serie in sentSeries" :key="serie.id">
                    <img :src="getPathImage(serie.poster_path)" alt="cover series image" class="image_poster" 
                    onerror="src='//lightwidget.com/wp-content/uploads/local-file-not-found.png'">
                    <h6> <strong>TITOLO: </strong>  {{ serie.name }}</h6>
                    <p> <strong>Titolo originale:</strong>  {{ serie.original_name }}</p>
                    <div class="flag"> 
                        <strong>Lingua originale: </strong> 
                        <img :src="getFlag(serie.original_language)" :alt="serie.original_language" 
                        onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'"> 
                        <span> {{serie.original_language}} </span>
                    </div>
                    <p> <strong>Voto: </strong> {{ serie.vote_average }}</p>
                </li>
            </ul>
        </div>
    </main>
</template>
  
<script>
  
  
export default {
    name: 'MainComponent',
    props: {
        sentFilms: Array,
        sentSeries: Array
    },
    methods: {
        getFlag(initials_flag) {
            console.log(initials_flag);
            if(initials_flag==='en') initials_flag='gb';        
            
            let string = 'https://www.bandiere-mondo.it/data/flags/w702/' + initials_flag + '.webp';
            console.log(string);
            return string;
        },
        getPathImage(path) {
            const string = 'https://image.tmdb.org/t/p/w500' + path;
            console.log(string);
            return string;
        },
        getStar(vote){
            let new_vote=parseInt( Math.floor(vote/2) );
            console.log("NEW VOTE: ", new_vote);
        },
    }
    
}
</script>
  
<style lang="scss" scoped>
li {
    list-style-type: none;
    border: 2px solid #fff;
    border-radius: 5px;
    padding: 15px;
}
.flag {
    img {
        width: 30px;
    }
}

.image_poster {
    width: 100%;
}
.cards {
    display: flex;
    flex-wrap: wrap;
}
.card {
    width: calc(100% / 5);
    background-color: black;
}
</style>
  