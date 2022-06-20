<template>
	<div class="wrapper">
		<div class="card" @click="selectItem()" :class="{ card_selected: selected, disabled: !product.inStock  }">
			<div class="card__header">
				<span>Сказочное заморское яство</span>
			</div>
			<div class="card__body">
				<div class="card__title">
					<h1>{{ product.title }}</h1>
				</div>
				<div class="card__subtitle">
					<h3>{{ product.flavor }}</h3>
				</div>
				<div class="card__subtle">
					<p><span class="card__quantity">{{ product.quantity }}</span> порций</p>
					<p v-if="product.mice == 1">мышь в подарок</p>
					<p v-if="product.mice > 1 && product.mice < 5"><span class="card__quantity">{{ product.mice }}</span> мыши в подарок</p>
					<p v-if="product.mice >= 5"><span class="card__quantity">{{ product.mice }}</span> мышей в подарок</p>
					<p v-if="product.quantity >= 100">заказчик доволен</p>
				</div>
			</div>
			<div class="card__weight"><span>{{ product.weight }}</span><br />кг</div>
		</div>
		<div class="card_bottom">
			<p v-if="!product.inStock"><span class="error">Печалька, {{ product.flavor}} закончился.</span></p>
			<p v-else-if="!selected">Чего сидишь? Порадуй котэ, <span><span class="link" @click="selectItem()">купи</span>.</span></p>
			<p v-else>{{ product.desc }}</p>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			product: Object
		},
		data() {
			return {
				selected: false,
			};
		},
		methods: {
			selectItem() {
				if (this.product.inStock) {
					this.selected = !this.selected
				}
			}
		},
	}
</script>

<style lang="scss">

$color-primary: #1698D9;
$color-primary-active: #2EA8E6;
$color-primary-dark: #22A7E9;
$color-primary-disabled: #979797;
$color-selected: #D91667;
$color-selected-active: #E52E7A;
$color-secondary: #666666;
$color-secondary-disabled: #B3B3B3;
$color-error: #FFFF66;

.card {
	background-color: #F2F2F2;
	height: 480px;
	width: 320px;
	padding: 0 48px;
	border-radius: 12px;
	background-image: url('../assets/cat.svg');
	background-repeat: no-repeat;
	background-position: bottom -4px left -4px;
	border: 4px solid $color-primary;
	position: relative;
	cursor: pointer;
	overflow: hidden;
	-webkit-clip-path: polygon(43px 0, 100% 0, 100% 100%, 0 100%, 0 43px);
	clip-path: polygon(43px 0, 100% 0, 100% 100%, 0 100%, 0 43px);

	&::after {
		content: "";
		position:absolute;
		top: -68px;
		left: -68px;
		width:100px;
		height:100px;
		transform:rotate(45deg);
		box-shadow: 0 0 0 5px $color-primary;
	}

	&__header {
		font-size: 16px;
		color: $color-secondary;
		margin-top: 20px;
	}

	&__title h1 {
		font-size: 48px;
		font-weight: 700;
		margin-left: -2px;
	}

	&__subtitle {
		font-size: 24px;
		font-weight: 700;
	}

	&__quantity {
		font-weight: 700;
	}

	&__subtle {
		font-size: 14px;
		color: $color-secondary;
		margin-top: 15px;
		line-height: 16px;
	}

	&__weight {
		width: 80px;
		height: 80px;
		position: absolute;
		background-color: $color-primary;
		text-align: center;
		color: #fff;
		border-radius: 50%;
		line-height: 22px;
		font-size: 21px;
		padding-top: 20px;
		bottom: 12px;
		right: 12px;

		& span {
			font-size: 42px;
		}
	}

	&:hover {
		border-color: $color-primary-active;

		&:after {
			box-shadow: 0 0 0 5px $color-primary-active;
		}

		& .card__weight {
			background-color: $color-primary-active;
		}
	}

	&_selected {
		border-color: $color-selected;

		&:after {
			box-shadow: 0 0 0 5px $color-selected;
		}

		& .card__weight {
			background-color: $color-selected;
		}
	}

	&_selected:hover {
		border-color: $color-selected-active;

		&:after {
			box-shadow: 0 0 0 5px $color-selected-active;
		}

		& .card__weight {
			background-color: $color-selected-active;
		}
	}

	&_selected:hover &__header::before {
		content: 'Котэ не одобряет?';
		color: #E62E7A;
	}

	&_selected:hover &__header span {
		display: none;
	}

	&_bottom {
		color: #fff;
		text-align: center;
		font-size: 13px;
		margin-top: 14px;
		margin-bottom: 40px;
		width: 320px;

		& span {
			color: $color-primary-dark;
		}

		& .link {
			text-decoration: underline;
			text-decoration-style: dashed;
			cursor: pointer;
		}
	}
}

.disabled {
	color: $color-secondary-disabled;
	pointer-events: none;
	background-image: url('../assets/cat-disabled.svg');
	border: 4px solid $color-secondary-disabled;

	&::after {
		box-shadow: 0 0 0 5px $color-secondary-disabled;
	}

	& .card__header {
		color: $color-secondary-disabled;
	}
 
	& .card__subtle {
		color: $color-secondary-disabled;
	}

	& .card__weight {
		background-color: $color-secondary-disabled;
	}
}

.error {
	color: $color-error !important;
}



</style>