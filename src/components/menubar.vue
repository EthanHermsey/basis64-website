<template>

	<div id="menubar">

		<a href="/"><h1>BASIS64</h1></a>

		<div id="menuitems" :style="{gridTemplateRows: `repeat(${this.itemData.length}, auto)`}">


			<p v-on:click="scrollTo(index)" v-for="(item, index) in itemData" :key="item.title">
					{{ item.title }}
			</p>

		</div>

		<div id="email">ethan@basis64.nl</div>

	</div>

</template>

<script>

export default {

	props: {

		itemData: []

	},
	methods: {
		scrollTo( index ) {

			this.$emit( 'scroll', index );

		}
	}

};

</script>


<style scoped>

	#menubar{

		position: fixed;

		top:0;
		left: 0;
		width: 10vw;
		height: 100vh;

		background-color: var(--sec-bg-color);

	}

	a{

		text-decoration: none;
		color: var(--line-color);

	}

	h1{

		margin: 0px;
		margin-left: 10px;

		height: 8vh;

		font-family: 'EunomiaLight';
		font-weight: 700;
		font-size: min( 8vh, 3.5vw );

	}

	#menuitems{

		margin-left: 10px;
		height: 87vh;

		display: grid;
		grid-template-columns: 100%;
		grid-template-rows: repeat(28, auto);

		text-transform: capitalize;

	}

	p{

		margin: 0;

		color: var(--line-color);
		font-size: min( 1.8vh, 1vw );
	}

	#menuitems p:hover{
		text-decoration: underline;
		cursor: pointer;
	}

	#email{
		position: fixed;

		left: 0;
		bottom: 5px;
		width: 10vw;

		color: var(--sec-line-color);

		font-size: min(1.2vw, 1em);
		text-align: center;
		user-select: text;
	}

	@media only screen and (max-width: 999px) {

		#menubar{

			position: fixed;
			z-index: 10;

			margin: 0px;

			top: 0;
			width: calc( 100vw - 10px);
			height: 50px;

		}

		h1{
			margin: 0px;
			margin-left: 25px;
			margin-top: -5px;


			color: var(--line-color);
			font-family: 'EunomiaLight';
			font-weight: 700;
			font-size: 40px;
		}

		#menuitems{

			display: none

		}

		#email{

			top: 10px;

			width: calc( 100vw - 15px );
			height: 65px;

			text-align: right;

			font-size: 1em;

		}

	}

</style>
