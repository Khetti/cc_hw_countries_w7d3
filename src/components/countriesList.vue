<template>
  <div>
    <ul>
      <list-country v-for="(country, index) in countries" :country="country"
       :key="index"></list-country>
    </ul>
  </div>
</template>
<script>
import listCountry from './listCountry.vue';
export default {
  name: 'countries-list',
  props: ['countries'],
  components:{
    "list-country": listCountry
  }

}
</script>
<style lang="css" scoped>
</style>
