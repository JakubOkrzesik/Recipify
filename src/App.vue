<template>
  <h1>Recipify</h1>
  <div>
    <IngredientsForm :recipes="recipes" @setRecipes="setRecipes"></IngredientsForm>
    <RecipeBlockHandler :recipes="recipes"></RecipeBlockHandler>
  </div>
</template>

<script>
import IngredientsForm from './components/IngredientsForm.vue';
import RecipeBlockHandler from './components/RecipeBlockHandler.vue';

export default {
  name: 'App',
  data(){
    return {
      recipes: [],
    }
  },
  methods: {
    setRecipes(newRecipes){
      this.recipes = newRecipes
    }
  },
  components: {
    IngredientsForm,
    RecipeBlockHandler
  }
};
</script>

<style>
*{
  font-family: monospace;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  background-color: #FFEEDB;
}
</style>
