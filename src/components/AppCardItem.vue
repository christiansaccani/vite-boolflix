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
            <p class="card-otitle">{{ film.original_title }}</p>
            <p class="card-lang">{{ film.original_language }}</p>
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