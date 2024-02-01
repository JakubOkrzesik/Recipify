<template>
  <div class="block">
    <ul class="block-list">
      <img :src=image_link class="image">
      <li class="title">{{ title }}</li>
      <li class="kcal">{{ kcal }} kcal</li>
      <a class="link" :href=link target="_blank">Recipe Link</a>
    </ul>
  </div>
</template>
<script>

export default {
  name: 'RecipeBlock',
  props: ["image_link","title","kcal","link"],
  components: {
  },
};
</script>
<style>
.block {
  background-color: #ED9B40;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 2%;
  width: 25%;
  padding: 20px;
  box-sizing: border-box;
  border-radius: 25px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-left: auto; 
  margin-right: auto; 
}

.block-list {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  text-align: center;
}

.image {
  max-width: 100%;
}

.title,
.kcal,
.link {
  margin: 5px 0;
}

.link {
  color: white;
  text-decoration: none;
  font-weight: bold; 
  display: inline-block;
  padding: 5px 10px;
  border: 1px solid white;
  border-radius: 5px;
}

.link:hover {
  background-color: white;
  color: #466362;
}
</style>
