<template>
  <div
    :style="{ backgroundColor: setBgColor, border: setBgColor }"
    class="overflow-hidden rounded shadow-lg my-3 my-md-auto cursor-pointer"
    @click="$router.push(`/country/${country.name}`)"
  >
    <img
      :src="country.flag"
      class="flag w-100"
      height="200"
      alt="country image"
    >
    <div class="pl-4 py-4">
      <h4 class="font-18 font-weight-bold">
        {{ country.name }}
      </h4>
      <p class="font-14">
        <span class="d-block py-1">
          population : {{ formatPopulation(country.population) }}
        </span>
        <span class="d-block py-1"> Region : {{ country.region }} </span>
        <span class="d-block py-1"> Capital : {{ country.capital }} </span>
      </p>
    </div>
  </div>
</template>

<script>
import global from '~/mixins/global.js'
export default {
  mixins: [global],
  props: {
    country: {
      type: Object,
      required: true
    }
  },
  computed: {
    setBgColor () {
      return this.$nuxt.$colorMode.preference === 'dark'
        ? 'hsl(209, 23%, 22%)'
        : 'hsl(0, 0%, 100%)'
    },
    setTextColor () {
      return this.$nuxt.$colorMode.preference === 'dark'
        ? 'hsl(0, 0%, 100%)'
        : 'hsl(200, 15%, 8%)'
    }
  }
}
</script>

<style>
.flag {
  object-fit: cover;
}
</style>
