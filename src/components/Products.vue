<template>
	<div class="card-list">
		<Item v-for="product in products" :key="product.id" :product="product" />
	</div>
</template>

<script>
import Item from './Item.vue';
	export default {
    components: { Item },
		props: {
			products: Array
		},
		data() {
			return {
				products: [
					{
						id: 0,
						title: 'Нямушка',
						flavor: 'с фуа-гра',
						weight: '0,5',
						quantity: 10,
						mice: 1,
						desc: 'Печень утки разварная с артишоками.',
						inStock: true
					},
					{
						id: 1,
						title: 'Нямушка',
						flavor: 'с рыбой',
						weight: '2',
						quantity: 40,
						mice: 2,
						desc: 'Головы щучьи с чесноком да свежайшая сёмгушка.',
						inStock: true
					},
					{
						id: 2,
						title: 'Нямушка',
						flavor: 'с курой',
						weight: '5',
						quantity: 100,
						mice: 5,
						desc: 'Филе из цыплят с трюфелями в бульоне.',
						inStock: false
					},
				]
			}
		}
}
</script>

<style lang="scss">

.card-list {
	display: grid;
	grid-template-columns: repeat(1, 320px);
  justify-content: space-evenly;
	margin-top: 40px;
}

@media screen and (min-width: 768px) {

	.top-header h1 {
		font-size: 36px;
	}

	.card-list {
		grid-template-columns: repeat(4, 1fr)
	}

	.card-list .wrapper {
		grid-column: span 2;
		margin: 0 auto;
	}

	.card-list .wrapper:nth-last-child(1):nth-child(odd) {
		grid-column: 2 / span 2;
	}



}
@media screen and (min-width: 1024px) {
	.card_bottom {
		margin-bottom: 0;
	}

	.container {
		align-content: center;
	}

	.card-list {
		grid-template-columns: repeat(3, 320px);
	}

	.card-list .wrapper {
		grid-column: auto;
	}

	.card-list .wrapper:nth-last-child(1):nth-child(odd) {
		grid-column: auto;
	}
}
</style>