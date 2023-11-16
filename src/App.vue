<template>
    <div class="">
        Задача 5. Спробуйте відтворити фрагмент. Компонент ProductsFilters через v-model повертає 2 значення фільтра:<br />
        продавець, бренд. При заданні модифікатора “check” відображати секцію зеленою рамкою, якщо фільтр з <br />
        відповідної секції (продавець чи бренд) не обрано.
    </div>
    <products-cards-manager :products-list-data="notebooksList"/>
</template>

<script>
import ProductsCardsManager from './components/ProductsCardsManager.vue';
import { notebooksList } from './constants/data'
export default {
    name: 'App',
    components: { ProductsCardsManager },
    data() {
        return {
            notebooksList,
        }
    },
}
</script>

<style lang="scss">
@import './assets/styles/index' ;
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
