<template>
	<div class="container">
		<h1 class="top-header">
			<h1>Ты сегодня покормил кота?</h1>
		</h1>
		<Products />
	</div>
</template>

<script>
import Products from './components/Products.vue';

export default {
  name: 'App',
  components: {
    Products
}
}
</script>

<style lang="scss">

.top-header {
	font-family: 'Exo 2', sans-serif;
	color: #fff;
	font-size: 28px;
	text-align: center;
	margin-top: 40px;
}

.container {
	max-width: 1280px;
	margin: 0 auto;
	display: grid;
	height: 100vh;
}

</style>
