<script>
export default {
    name: 'AppCardItem',

    props: {
        film: Object,
    },
}


</script>

<template>
    <li v-if="film.media_type === 'movie'">
        <div class="cover">
            <img class="poster-img" :src="'https://image.tmdb.org/t/p/w342' + (film.poster_path)"
            onerror="this.src='./public/white.jpg'"/>

            <div class="card-info">
                <p class="card-title">{{ film.title }}</p>

                    <img class="flag-info" 
                    :src="'https://flagcdn.com/w20/' + (film.original_language === 'en' ? 'us'
                        : film.original_language === 'ko' ? 'kr'
                        : film.original_language === 'ja' ? 'jp'
                        : film.original_language === 'zh' ? 'cn'
                        : film.original_language) + '.png'"
                    :alt="film.original_language"
                    onerror="this.src='./public/world.png'"/>

                    <p class="card-otitle">{{ film.original_title }}</p>
                    <i v-for="index in 5" :class="['fas', 'fa-star', {'filled': index <= Math.ceil(film.vote_average / 2)}, {'empty': index > Math.ceil(film.vote_average / 2)}]" :key="index"></i>
                
                    <p class="card-plot">{{ film.overview }}</p>

            </div>
        </div>
    </li>

    <li v-else-if="film.media_type === 'tv'">
        <div class="cover">
            <img class="poster-img" :src="'https://image.tmdb.org/t/p/w342' + (film.poster_path)"
            onerror="this.src='./public/white.jpg'"/>
            
            <div class="card-info">
                <p class="card-title">{{ film.name }}</p>

                    
                    <img class="flag-info"
                    :src="'https://flagcdn.com/w20/' + (film.original_language === 'en' ? 'us'
                        : film.original_language === 'ko' ? 'kr'
                        : film.original_language === 'ja' ? 'jp'
                        : film.original_language === 'zh' ? 'cn'
                        : film.original_language) + '.png'"
                    :alt="film.original_language"
                    onerror="this.src='./public/world.png'"/>

                    <p class="card-otitle">{{ film.original_name }}</p>
                    <i v-for="index in 5" :class="['fas', 'fa-star', {'filled': index <= Math.ceil(film.vote_average / 2)}, {'empty': index > Math.ceil(film.vote_average / 2)}]" :key="index"></i>

                    <p class="card-plot">{{ film.overview }}</p>

            </div>
        </div>
    </li>
</template>

<style lang="scss" scoped>

@use '../style/variables' as *;

li {

    max-width: 18vw;
    min-width: 300px;

    margin-right: 5px;

    .cover {

        position: relative;
        height: 450px;
        background-color: #0c0c0c;

        .poster-img {

        width: 100%;
        min-width: 300px;
        height: 450px;
        object-fit: cover;

        margin-bottom: .5em;
        margin-right: 10px;
        overflow-x: auto;
        }

        .card-info {

            position: absolute;
            top: 1em;
            left: 1em;

            opacity: 0;
    
            .card-title {
                font-size: large;
                font-weight: 500;

                max-width: 12vw;
                min-width: 260px;

                padding-bottom: .5em;
                border-bottom: 1px solid $primaryColor;

                white-space: nowrap;
                overflow: hidden;
                text-overflow: ellipsis;
            }

            .card-media {
                font-weight: 700;
                font-size: 14px;
            }

            .flag-info {
                margin-top: .5em;
                max-width: 20px;
                margin-right: 1em;
            }

            .card-otitle {
                font-style: italic;
                font-size: 14px;
                margin-bottom: .5em;
            }

            .card-vote {
                color: #00c05d;
            }

            .fa-star.filled {
                color: $primaryColor;
            }

            .fa-star.empty {
                color: rgba(255, 255, 255, 0.452);
            }

            .card-plot {
                margin-top: .75em;
                max-height: 300px;
                overflow-y: auto;
                max-width: 14.5vw;
                padding-right: .5em;

                &::-webkit-scrollbar {
                    width: 8px; /* Larghezza della scrollbar */
                    background-color: rgba(255, 255, 255, 0.2); /* Colore di sfondo della scrollbar */
                    border-radius: 4px;
            }

            }
        }
    }
}

.cover:hover .card-info {
        opacity: 1; // Mostra le scritte al passaggio del mouse sull'elemento .cover
    }

.cover:hover .poster-img{
                opacity: 0.1;
            }

</style>