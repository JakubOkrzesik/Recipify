<template>
    <div>
       <RecipeBlock v-for="item, index in recipes" :key="index" v-bind="item"/>
    </div>
</template>
<script>
import RecipeBlock from './RecipeBlock.vue';

export default {
  name: 'RecipeBlockHandler',
  props: ["recipes"],
  components: {
    RecipeBlock,
  },
};
</script>
<style>

</style>
