<template>
  <li v-on:click="handleClick"> {{country.name}} </li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: "list-country",
  props: ['country'],
  methods: {
    handleClick(){
      eventBus.$emit('country-selected', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
