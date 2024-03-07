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
        <p class="card-title">{{ film.title }}</p>
        <section>
            

            <img 
            :src="'https://flagcdn.com/w20/' + (film.original_language === 'en' ? 'us'
                : film.original_language === 'ko' ? 'kr'
                : film.original_language === 'ja' ? 'jp'
                : film.original_language === 'zh' ? 'cn'
                : film.original_language) + '.png'"
            :alt="film.original_language"
            onerror="this.src='./public/world.png'"/>

            <p class="card-media">movie</p>
            <p class="card-otitle">{{ film.original_title }}</p>
            <p class="card-vote">{{ (film.vote_average).toFixed(2) }}</p>
        </section>
    </li>

    <li v-else-if="film.media_type === 'tv'">
        <p class="card-title">{{ film.name }}</p>
        <section>
            

            <img 
            :src="'https://flagcdn.com/w20/' + (film.original_language === 'en' ? 'us'
                : film.original_language === 'ko' ? 'kr'
                : film.original_language === 'ja' ? 'jp'
                : film.original_language === 'zh' ? 'cn'
                : film.original_language) + '.png'"
            :alt="film.original_language"
            onerror="this.src='./public/world.png'"/>

            <p class="card-media">series</p>
            <p class="card-otitle">{{ film.original_name }}</p>
            <p class="card-vote">{{ (film.vote_average).toFixed(2) }}</p>
        </section>
    </li>
</template>

<style lang="scss" scoped>

@use '../style/variables' as *;

li {
    width: 20vw;
    padding: .5em;

    .card-title {
        font-size: large;
        font-weight: 500;

        padding-bottom: .50em;
        border-bottom: 1px solid $primaryColor;

        white-space: nowrap;
        overflow: hidden; // Nasconde il testo che supera le dimensioni disponibili
        text-overflow: ellipsis;
    }

    section {
        padding-top: .5em;

        .card-media {
            font-weight: 700;
            font-size: 14px;
        }

        img {
            max-width: 20px;
            margin-right: 1em;
        }

        .card-otitle {
            font-style: italic;
            font-size: 14px;
            padding-top: .4em;
        }

        .card-vote {
            color: #00c05d;
        }
    }
}

</style>