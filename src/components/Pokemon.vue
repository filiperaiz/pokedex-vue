<template lang="html">
    <main class="pokemon__content">
        <div class="pokemon__search">
            <label class="pokemon__search-label" for="search">Pesquise pelo nome do pokémon</label>
            <input class="pokemon__search-input" v-model="search" type="text">
        </div>

        <article class="pokemon__list">
            <pokemon-card v-for="pokemon in pokemonList" :key="pokemon.name" :pokemon="pokemon"></pokemon-card>
            
            <div class="noresult" v-if="pokemonList.length == 0">
                <h3>Nenhum pokémon foi encontrado</h3>
                <img src="../assets/noresult.png" alt="" width="200">
            </div>
        </article>
    </main>
</template>

<script lang="js">
    import axios from "axios";
    import PokemonCard from "./PokemonCard.vue";

    export default {
        components: {
            PokemonCard
        },

        data() {
            return {
                pokemons: [],
                search: ""
            };
        },

        mounted() {
            this.getPokemons();
        },

        computed: {
            pokemonList() {
                return this.pokemons.filter(pokemon => {
                    return pokemon.name
                        .toLowerCase()
                        .includes(this.search.toLowerCase());
                });
            }
        },

        methods: {
            getPokemons(url = "https://api.myjson.com/bins/dth9z") {
                axios.get(url).then(response => {
                    this.pokemons = response.data;
                });
            }
        }
    };
</script>

<style lang="scss">
.pokemon {
    &__search {
        display: flex;
        flex-direction: column;
        justify-content: center;
        flex-wrap: nowrap;
        max-width: 400px;
        margin: 40px auto;

        &-label {
            font-size: 16px;
            font-weight: bold;
        }

        &-input {
            width: 100%;
            height: 45px;
            border: 2px solid #30a7d7;
            border-radius: 4px;
            margin: 8px 0;
            outline: none;
            padding: 10px;
            font-size: 16px;
            box-sizing: border-box;
            transition: 0.3s;

            &:focus {
                border-color: #30a7d7;
                box-shadow: 0 0 8px 0 dodgerBlue;
            }
        }
    }

    &__list {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
        align-content: flex-start;
        align-items: flex-start;

        @media screen and (max-width: 600px) {
            flex-direction: column;
            justify-content: flex-start;
            align-content: center;
            align-items: center;
        }
    }
}
</style>