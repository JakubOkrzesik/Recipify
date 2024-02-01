<template>
    <div class="tab">
        <ul class="textarea" v-for="ingr,index in array" :key="index">
            <li>{{ ingr }}</li>
        </ul>
    </div>
</template>
<script>

export default {
  name: 'IngredientsTab',
  props: ['array'],
};
</script>
<style>
.tab {
    background-color: #AA8F66;
    padding: 15px;
    border-radius: 8px;
}

.textarea {
    list-style-type: none;
    margin: 0;
    padding: 0;
    text-align: center;
}

.textarea li {
    color: #4C4C4C;
    font-weight: 500;
    margin-bottom: 8px;
}
</style>
