<template>
<div id="app">
    <iTune />
</div>
</template>

<script>
import iTune from './components/iTune.vue'
export default {
    name: 'App',
    components: {
        iTune

    }
}
</script>

<style>
#app {
    font-family: 'Athiti', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    margin-top: 60px;
}

body {
    background-image: url('https://i.pinimg.com/originals/bc/55/51/bc5551ac237a9ef4d8e9575662f2e106.gif');
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
