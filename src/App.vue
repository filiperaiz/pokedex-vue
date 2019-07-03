<template lang="html">
    <div id="app">
        <header class="header">
            <img class="header__logo" src="./assets/logo.png" />
        </header>

        <main class="main">
            <pokemon></pokemon>
        </main>
    </div>
</template>

<script lang="js">
    import Pokemon from "./components/Pokemon";

    export default {
        name: "app",
        components: {
            Pokemon
        }
    };
</script>

<style lang="scss">
body {
    margin: 0;
    background: #fff url(./assets/bg.png);
}

*,
*:before,
*:after {
    box-sizing: border-box;
}

#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;

    @media screen and (max-width: 600px) {
        padding: 0 20px;
    }
}

.header {
    padding: 40px 0;

    &__logo {
        width: 250px;
    }
}

.main {
    width: 100%;
    max-width: 860px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0 auto 40px;
    padding: 10px;
    border-radius: 4px;
    background-color: #fff;
    border: 2px solid #30a7d7;
}
</style>