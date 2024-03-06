<script>
export default {

    name: 'AppNav',

    data() {
        return {
            searchText: ''
        };
    },

    methods: {
        search() {
            this.$emit('search', this.searchText);
        }
    }

}
</script>

<!-- ---------------------------------------------------------------------------------- -->

<template>

    <nav>
        <div id="logo">
            BOOLFLIX
        </div>
        <div id="search-bar">
            <input type="search" name="searchText" v-model="searchText" placeholder="es. Maze Runner">
            <button @click="search" class="btn">Cerca</button>
        </div>
    </nav>

</template>

<!-- ---------------------------------------------------------------------------------- -->

<style lang="scss">

nav {
    display: flex;
    justify-content: space-between;
    align-items: center;

    padding: 1em;
    background-color: #0c0c0c;

    #logo {
        font-size: x-large;
        font-weight: bold;
        color: red;
    }

    #search-bar {
        display: flex;
        gap: 1em;

        input {
            padding: 6px 10px;
        }

        button {
            padding: 6px 10px;
        }
    }
}

</style>