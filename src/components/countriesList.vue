<template>
  <div>
    <!-- <select>
      <list-country v-for="(country, index) in countries" :country="country"
        :key="index"></list-country>
    </select> -->
    <ul>
      <list-country v-for="(country, index) in countries" :country="country"
       :key="index"></list-country>
     </ul>
  </div>
</template>

<script>
import ListComponent from './ListComponent.vue';
export default {
  name: 'countries-list',
  props: ['countries'],
  components:{
    "list-country": ListComponent
  }
}
</script>

<style lang="css" scoped>
</style>
