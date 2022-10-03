<template>
    <main class="row mt-4">
        <!-- FILMS -->
        <div class="films">
            <h1> FILM: </h1>
            <ul class="cards">
                <li class="card" v-for="film in sentFilms" :key="film.id">
                    <img :src="getPathImage(film.poster_path)" alt="cover film image" class="image_poster"
                        onerror="src='//lightwidget.com/wp-content/uploads/local-file-not-found.png'">
                    <p class="card-overview"> {{ film.overview }} </p>
                    <h6> <strong>TITOLO: </strong> {{ film.title }}</h6>
                    <p> <strong>ORIGINAL:</strong> {{ film.original_title }}</p>
                    <div class="flag">
                        <strong>LINGUA: </strong>
                        <img :src="getFlag(film.original_language)" :alt="film.original_language"
                            onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'">
                        <span> {{film.original_language}} </span>
                    </div>
                    <p class="card-vote"> <strong>VOTO: </strong>
                        <i v-for="n in 5" :key="n" class="fa-star"
                            :class="( n <= Math.ceil(film.vote_average/2) )?'fa-solid':'fa-regular'"></i>
                    </p>
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
                    <p class="card-overview"> {{ serie.overview }} </p>
                    <h6 class="card-title"> <strong>TITOLO: </strong> {{ serie.name }}</h6>
                    <p class="card-original-title"> <strong>ORIGINAL:</strong> {{ serie.original_name }}</p>
                    <div class="card-language flag">
                        <strong>LINGUA: </strong>
                        <img :src="getFlag(serie.original_language)" :alt="serie.original_language"
                            onerror="this.src = '//www.publicdomainpictures.net/pictures/280000/nahled/not-found-image-15383864787lu.jpg'">
                        <span> {{serie.original_language}} </span>
                    </div>
                    <p class="card-vote"> <strong>VOTO: </strong>
                        <i v-for="n in 5" :key="n" class="fa-star"
                            :class="( n <= Math.ceil(serie.vote_average/2) )?'fa-solid':'fa-regular'"></i>
                    </p>
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
            stars: [],
        }
    },
    props: {
        sentFilms: Array,
        sentSeries: Array
    },
    methods: {
        getFlag(initials_flag) {
            // console.log(initials_flag);
            if (initials_flag === 'en') initials_flag = 'gb';

            let string = 'https://www.bandiere-mondo.it/data/flags/w702/' + initials_flag + '.webp';
            // console.log(string);
            return string;
        },
        getPathImage(path) {
            const string = 'https://image.tmdb.org/t/p/w500' + path;
            // console.log(string);
            return string;
        },

        /* 
        getStar(vote, iWantToReturn){
            // PASSA DA MAX VALUTATION 10 A MAX VALUTATION 5
            let new_vote=parseInt( Math.ceil(vote/2) );
            // RIAZZERA L'ARRAY PER POTER RIESEGUIRE IL CALCOLO PER OGNI CARD
            this.stars=[];
            // RIEMPI L'ARRAY STARS TANTE VOLTE QUANTE SONO LE STELLE PIENE
            for(let i=0; i<new_vote; i++) {
                this.stars[i]='';
            }
            // FUNZIONALITA' AGGIUNTIVA: RESTITUISCI OPPURE NO IL VOTO (1/0)
            if(iWantToReturn===1){
                return new_vote;
            }
        }
        */
    }

}
</script>
  
<style lang="scss" scoped>
main {
    padding-top: 90px;
}

li {
    list-style-type: none;
    border: 2px solid rgb(23, 23, 23);
    margin: 2px 2px;
    border-radius: 5px;
    padding: 8px;
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
    width: calc(100% / 5 - 4px);
    background-color: black;
    opacity: 0.7;

    strong {
        font-size: 0.8rem;
        color: grey;
    }
}

.card:hover {
    opacity: 1;
    transform: scale(103%);
    transition: transform 200ms;
}

.card:hover .image_poster {
    // togli l'immagine poster
    display: none;
}

.card:hover .card-overview {
    // rendi visibile overview
    display: block;

}
.card-overview {
    height: 320px;
    overflow-y: auto;
    display: none;
}
</style>
  