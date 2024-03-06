<script>
export default {
    name: 'AppCardItem',

    props: {
        film: Object,
    },
}
</script>

<template>
    <li>
        <p class="card-title">{{ film.title }}</p>
        <section>
            <p class="card-lang">{{ film.original_language }}</p>
            <img :src="'https://flagcdn.com/w20/' + (film.original_language === 'en' ? 'us'
            : film.original_language === 'ko' ? 'kr'
            : film.original_language === 'ja' ? 'jp'
            : film.original_language) + '.png'">
            <p class="card-otitle">{{ film.original_title }}</p>
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
        .card-otitle {
            font-style: italic;

            padding-top: .5em;
        }

        .card-vote {
            color: #00c05d;
        }
    }
}

</style>