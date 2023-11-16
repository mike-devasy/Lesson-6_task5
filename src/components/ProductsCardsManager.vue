<template>
    <div class="product-cards">
        <div class="product-cards__filter">
            <products-filters
                v-model:sellers.check="filters.sellers"
                v-model:brands.check="filters.brands"
                :cards-data="productsListData"
            />
        </div>
        <div class="product-cards__list">
            <div class="product-cards__item">
                <card-product v-for="note in selectedCardProducts" :key="note.id" :note-data="note" />
            </div>
        </div>
    </div>
</template>

<script>
import CardProduct from './CardProduct.vue'
import ProductsFilters from './ProductsFilters.vue'
export default {
    name: 'ProductsCardsManager',
    components: { CardProduct, ProductsFilters },
    props: {
        productsListData: {
            type: Array,
            default: () => [],
        },
    },
    data() {
        return {
            filters: {
                sellers: [],
                brands: [],
            },
        }
    },
    computed: {
        isSellerSelected() {
            return this.filters.sellers.length > 0
        },
        isBrandSelected() {
            return this.filters.brands.length > 0
        },
        selectedCardProducts() {
            return this.productsListData.filter((note) => this.isCardSelected(note))
        },
    },
    methods: {
        isCardSelected(note) {
            return this.matchSellerFilter(note) && this.matchBrandFilter(note)
        },
        matchSellerFilter(note) {
            return !this.isSellerSelected || this.filters.sellers.includes(note.seller)
        },
        matchBrandFilter(note) {
            return !this.isBrandSelected || this.filters.brands.includes(note.brand)
        },
    },
}
</script>

<style lang="scss" scoped>
.product-cards {
display: flex;
gap:20px;
&__filter {
	padding-top: 100px;
	width: 300px;
	flex:0 1 25%
}

&__list {
	flex:0 1 75%
}

&__item {
}
}
</style>
