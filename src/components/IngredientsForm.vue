<template>
    <div class="container">
        <label for="ingrform">Type in your desired ingredient one by one</label>
        <input type="text" id="ingrform" name="ingrform" v-model="ingredient">
        <button @click="submit(ingredient)" type="submit">Submit</button>
        <div v-if="ingredients.length!==0" class="dataDiv">
          <IngredientsTab :array="ingredients"></IngredientsTab>
          <div class="buttons-container">
            <button @click="getData()" type="button">Get recipes</button>
            <button @click="clear()">clear</button>
          </div>
        </div>
    </div>
</template>
<script>
import IngredientsTab from './IngredientsTab.vue';

export default {
  name: 'IngredientsForm',
  props: {
    recipes: Array,
  },
  components: {
    IngredientsTab,
  },
  data() {
    return {
      ingredients: [],
      ingredient: '',
    };
  },
  methods: {
    submit(ingr) {
      if (ingr !== '') {
        this.ingredients.push(ingr);
        this.ingredient = '';
      }
    },
    getData() {
      const appId = process.env.VUE_APP_APP_ID;
      const appKey = process.env.VUE_APP_APP_KEY;

      try {
        fetch(`https://api.edamam.com/api/recipes/v2?type=any&q=${this.ingredients.join(', ')}&app_id=${appId}&app_key=${appKey}`)
          .then((response) => response.json())
          .then((json) => 
            this.$emit('setRecipes', json.hits.map((item) => 
            ({title: item.recipe.label,
            link: item.recipe.url,
            image_link: item.recipe.image,
            kcal: Math.ceil(item.recipe.calories) })) 
          ))
      } catch (error) {
        console.log(error);
      }
    },
    clear(){
      this.$emit('setRecipes',[])
      this.ingredients=[]
    }
  },
};
</script>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 20px;
}

.dataDiv {
  margin-top: 20px;
  border: 1px solid #ddd;
  padding: 20px;
  border-radius: 5px;
}

.buttons-container {
  margin-top: 10px;
  display: flex;
  gap: 10px;
}
</style>