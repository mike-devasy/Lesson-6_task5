<template>
	<div class="filters">
<div class="filters__sellers sellers-filter" :class="['border', sellersSelectedBorder]" > 
	<h3>Продавець</h3>
	<div v-for="(seller, index) in sellersArray" :key="seller"  class="sellers-filter__item">
		<input :id="'seller-'+ index"  v-model="selectedSellers"   :value="seller" type="checkbox">
		<label  :for="'seller-'+ index"   class="sellers-filter__label">{{ seller}}</label>
	</div>
 
</div>
<div class="filters__brands brands-filter"   :class="['border', brandsSelectedBorder]" >
	<h3>Бренд</h3>
	<div v-for="(brand, index) in brandsArray" :key="brand"   class="brands-filter__item">
		<input :id="'brand-' + index" v-model="selectedBrands" :value="brand"  type="checkbox">
		<label  :for="'brand-' + index" class="brands-filter__label">{{brand}}</label>
	</div>
	 
</div>
	</div>
</template>

<script>
	export default {
		name:'ProductsFilters',
props: {
	cardsData: {
		type: Array,
		default:()=>[] 
	},
	sellers:{
		type:Array,
		required:true
	},
	sellersModifiers:{
		type:Object,
		default:()=>({})
	},
	brands:{
		type:Array,
		required:true
	},
	brandsModifiers:{
		type:Object,
		default:()=>({})
	},
},
emits: ['update:sellers', 'update:brands'],
data(){
	return{
		selectedSellers:[],
		selectedBrands:[]
	};
},
computed:{
	sellersArray(){
		return [...new Set(this.cardsData.map(note => note.seller))]
	},
	brandsArray(){
		return [...new Set(this.cardsData.map(note => note.brand))]
	},
	brandsSelectedBorder(){
		if(this.brandsModifiers.check && this.selectedBrands.length === 0)
		{return 'green-border'}
		return ''
	},
sellersSelectedBorder(){
		if(this.sellersModifiers.check && this.selectedSellers.length === 0)
		{return 'green-border'}
		return ''
	},
},
watch:{
	selectedSellers(newVal){
		this.$emit('update:sellers', newVal)
	},
	selectedBrands(newVal){
		this.$emit('update:brands', newVal)
	},
}
	}
</script>

<style lang="scss" scoped>
.filters {
padding: 0 50px;
&__sellers {
	display: flex;
	flex-direction: column;
	align-items: start;
	margin-bottom: 50px;
	padding: 20px;
}

&__brands {
	display: flex;
	flex-direction: column;
	align-items: start;
	padding: 20px;

}
}
.sellers-filter {

&__item {
}

&__label {
}
}
.brands-filter {

&__item {
}

&__label {
}
}
.border{
	border-radius: 20px;
	border:6px solid grey;
}
.green-border{
	border-color: green;
}
</style>