<template>
    <div class="flex flex-wrap">
        <div v-for="game in gameName"  class="w-full sm:w-1/2 md:w-1/3 lg:w-1/3 xl:w-1/3 mb-4 bg-gray-500 " v-bind:key="game.id">
            <div v-on:click="showPing(game.ip)">
                <div class="bg-gray-400">
                    {{ game.name }}
                    <img class="object-cover h-full w-full mx-2" v-bind:src="require(`../../public/${game.img}`)">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import * as ping from '../assets/script/ping';
    import json from '../assets/gameList';

    export default {
        name: 'GameList',
        methods: {
            showPing(x) {
                ping(x).then(function(delta) {
                    /* eslint-disable no-console */
                    console.log('\n/****= GameList.vue:23\n', x);
                    alert(delta);
                }).catch(function(error) {
                    alert(String(error));
                });
            },
        },
        computed: {
            gameName() {
                return json.gameList.map((item) => {
                    return item;
                });
            }
        }
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
