<template>
<div>
    <input class="bg-gray-200 appearance-none border-2 border-red-600 bg-gray-800
      rounded w-3/6 py-2 px-4 text-red-300 leading-tight focus:outline-none placeholder-red-500
      focus:border-red-700 mb-6" type="text" placeholder="Search Hero" v-model="search" v-on:keyup="findHeroes">
    <div  class="grid grid-cols-4 gap-4 justify-center" >
        <div class="col-span-1 border border-gray-700 p-2 rounded-lg cursor-pointer hover:bg-gray-900" v-for="hero in results" :key="hero.id">
            <router-link :to="'/hero/' + hero.id">
                <div class="my-1 flex text-white overflow-hidden">
                    <img class="inline-block h-12 w-auto rounded-lg" :src="'http://cdn.dota2.com' + hero.img" alt="" />
                    <span class="ml-2 text-white leading-6 font-semibold mr-2">{{ hero.localized_name }}</span>
                    [
                    <ul v-for="role in hero.roles" :key="role">
                        <li v-text="role" class="text-white mx-1 text-md"></li>
                    </ul>
                    ]
                </div>
            </router-link>
        </div>
    </div>
    
</div>
</template>

<script>
    const heroes = require('@/assets/constants/heroes.json')

    export default {
        name: 'SearchHero',
        props: {
            //msg: String
        },
        data: function () {
            return {
                search: null,
                heroes: heroes,
                results: heroes
            };
        },
        methods: {
            findHeroes() {
              var items = this.heroes;
                var result = Object.keys(items)
                    .map(key => items[key]) // turn an array of keys into array of items.
                    .filter(item => item.localized_name.toLowerCase().includes(this.search.toLowerCase())) // filter that array,
                this.results = result;
            }
        }
    }
</script>