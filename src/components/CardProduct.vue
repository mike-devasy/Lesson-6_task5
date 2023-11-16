<template>
	<div class="card-container">
		<a class="card" :href="noteData.link">
		<div class="card__image">
		<img :src="noteData.imgSrc" alt="note">
		</div>
		<div class="card__title">{{ noteData.title }}</div>
		<div class="card__price"><span>{{noteData.price}}₴</span></div>
		</a>
	</div>
</template>

<script>
	export default {
		name:'CardProduct',
		props: {
			noteData: {
				type: Object,
				default:()=>({}) 
			},
		},
	}
</script>

<style lang="scss" scoped>
.card-container {
	padding: 50px 0px;
	width: 300px;
	display: inline-block;
	margin: 25px;
}
.card {
&__image{
width: 300px;
padding-bottom: 100px ;
}
    &__image img{
width: 100%;
    }

    &__title {
			padding-bottom: 50px;
    }

    &__price {
			font-size: 25px;
			color: red;
    }
}

</style>