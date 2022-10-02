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
                    <p> <strong>ORIGINAL:</strong>  {{ film.original_title }}</p>
                    <div class="flag"> 
                        <strong>LINGUA: </strong> 
                        <img :src="getFlag(film.original_language)" :alt="film.original_language" 
                        onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'"> 
                        <span> {{film.original_language}} </span>
                    </div>
                    <p> <strong>VOTO: </strong> {{ getStar(film.vote_average) }} </p>
                    <span> <i v-for="(star,index) in stars" :key="index" class="fa-solid fa-star inrow"></i> </span>
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
                    <h6 class="card-title"> <strong>TITOLO: </strong>  {{ serie.name }}</h6>
                    <p class="card-original-title"> <strong>ORIGINAL:</strong>  {{ serie.original_name }}</p>
                    <div  class="card-language flag"> 
                        <strong>LINGUA: </strong> 
                        <img :src="getFlag(serie.original_language)" :alt="serie.original_language" 
                        onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'"> 
                        <span> {{serie.original_language}} </span>
                    </div>
                    <p class="card-vote"> <strong>VOTO: </strong> {{ getStar(serie.vote_average) }} </p>
                    <span> <i v-for="(star,index) in stars" :key="index" class="fa-solid fa-star inrow"></i> </span>
                </li>
            </ul>
        </div>
        
    </main>
</template>
  
<script>
  
  
export default {
    name: 'MainComponent',
    data() {
        return {
            stars: []
        }
    },
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
            let new_vote=parseInt( Math.ceil(vote/2) );
            console.log("NEW VOTE: ", new_vote);

            this.stars=[];
            for(let i=0; i<new_vote; i++) {
                this.stars[i]='<i class="fa-solid fa-star"></i>';
            }
            return new_vote;
        },
    }
    
}
</script>
  
<style lang="scss" scoped>
li {
    list-style-type: none;
    border: 2px solid rgb(23, 23, 23);
    margin: 0 2px;
    border-radius: 5px;
    padding: 8px;
}
.flag {
    img {
        width: 30px;
    }
}

.image_poster {
    width: 220px;
}
.cards {
    display: flex;
    flex-wrap: wrap;
}
.card {
    width: calc(100% / 5 - 4px);
    background-color: black;

    strong {
        font-size: 0.8rem;
        color: grey;
    }
}

</style>
  