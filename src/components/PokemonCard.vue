<template lang="html">
   <div class="pokemon__card">
        <div class="pokemon__card-picture">
            <img  :src="pokemon.image" :alt="pokemon.name" />
        </div>

        <div class="pokemon__card-name">{{ pokemon.name }}</div>

        <div class="pokemon__card-types">
            <span class="type" :class="getType(type)" v-for="type in pokemon.types" :key="type">{{type}}</span>
        </div>
  
        <div class="pokemon__card-extras" >
            <ul>
                <li>
                    <b>Weight:</b>{{pokemon.weight}}
                </li>
                <li>
                    <b>Height:</b>{{pokemon.height}}
                </li>
                <li>
                    <b>Experience:</b>{{pokemon.experience}}
                </li>
                <li>
                    <b>Abilities:</b> 
                    <span class="ability" v-for="ability in pokemon.abilities" :key="ability">{{ability}}</span>
                </li>
            </ul>
        </div>
        
    </div>
</template>

<script lang="js">
    export default  {
        name: 'pokemon-card',
        props: {
            pokemon: Object,
        },
        
        data() {
            return {
                
            }
        },

        mounted() {

        },

        methods: {
            getType(type) {
                return {
                    'poison': type == 'poison',
                    'grass': type == 'grass',
                    'fire': type == 'fire',
                    'flying': type == 'flying',
                    'water': type == 'water',
                    'bug': type == 'bug',
                    'normal': type == 'normal',
                    'electric': type == 'electric'
                }
            }
        },

        computed: {

        }
    }
</script>

<style scoped lang="scss">
.pokemon {
    &__card {
        cursor: auto;
        width: 32%;
        transition: transform 0.3s ease-out;
        position: relative;

        @media screen and (max-width: 600px) {
            width: 100%;
        }

        &-name {
            font-size: 20px;
            text-transform: capitalize;
            font-weight: bold;
        }

        &-types {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-content: center;
            align-items: center;

            .type {
                border-radius: 4px;
                font-size: 12px;
                font-weight: bold;
                text-align: center;
                margin: 5px;
                padding: 3px 10px;
                text-transform: capitalize;

                &.poison {
                    background-color: #b97fc9;
                    color: #fff;
                }
                &.grass {
                    background-color: #9bcc50;
                    color: #212121;
                }

                &.fire {
                    background-color: #fd7d24;
                    color: #fff;
                }

                &.flying {
                    background-color: #3dc7ef;
                    color: #212121;
                }

                &.water {
                    background-color: #4592c4;
                    color: #fff;
                }

                &.bug {
                    background-color: #729f3f;
                    color: #fff;
                }

                &.normal {
                    background-color: #a4acaf;
                    color: #212121;
                }

                &.electric {
                    background-color: #eed535;
                    color: #212121;
                }
            }
        }

        &-extras {
            background-color: rgba(48, 168, 215, 0.9);
            opacity: 0;
            position: absolute;
            bottom: 0px;
            left: 0;
            right: 0;
            top: 0;
            transition: all 0.3s ease-out;

            ul {
                margin: 0;
                padding: 0;
                text-align: center;
                list-style: none;

                li {
                    padding: 5px 0;
                    font-size: 16px;
                    color: #fff;
                    font-weight: bold;
                }

                b {
                    margin-right: 5px;
                }

                span {
                    text-transform: capitalize;
                    margin-right: 5px;

                    &:not(:last-child) {
                        &:after {
                            content: ",";
                        }
                    }
                }
            }
        }

        &:hover {
            box-shadow: 0 0 2px #30a7d7;

            .pokemon__card-extras {
                opacity: 1;
                display: flex;
                justify-content: center;
                align-items: center;
                align-content: center;
            }
        }
    }
}
</style>
