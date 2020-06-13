<template>
  <div class="">
     <h2 class="text-2xl font-bold leading-7 text-red-500 sm:text-3xl sm:leading-9 sm:truncate mb-2">
      Dota 2 Counter pick
    </h2>
      <SearchHero></SearchHero>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchHero from '@/components/SearchHero.vue'

export default {
  name: 'Home',
  components: {
    SearchHero
  }
}
</script>
