<template>
  <div id="itemcontainer" :item="item" :class="`span${item.children.length}`">
	<h4>
		{{ item.title }}
	</h4>
	<div id="itemgrid" :class="`grid${item.children.length}`">
		<img v-on:click="show(itemIndex, childIndex)" v-for="(child, childIndex) in item.children" :key="child.title" :src="`./resources/${child.img}`" :alt="child.title">
	</div>

  </div>
</template>

<script>

export default {
	props: {
		item: Object,
		itemIndex: Number
	},
	methods: {
		show( iIndex, cIndex ) {

			this.$emit( 'show', { itemIndex: iIndex, childIndex: cIndex } );

		}
	}
};

</script>


<style scoped>

	#itemcontainer{

		width: 100%;
		padding-top: 10px;

		background-color: var(--sec-bg-color);

		color: var(--line-color);

		border-style: solid;
		border-width: 1px;
		border-color: var(--main-border-color);
		border-radius: 2px;

		transition: border 200ms ease-in-out;

	}
	#itemcontainer:hover{

		border-color: var(--sec-border-color);

	}

	.span1{
		grid-column: span 1;
	}
	.span2{
		grid-column: span 2;
	}
	.span3{
		grid-column: span 3;
	}
	.span4{
		grid-column: span 4;
	}


	h4{
		margin: 0;
		margin-left: 10px;

		font-size: 1.5vw;
		font-family: 'EunomiaLight';
		font-weight: 700;
	}


	#itemgrid{

		min-height: 240px;
		width: 98%;
		margin-left: 1%;

		display: grid;
		column-gap: 10px;
		place-items: center;

	}

	.grid1{
		grid-template-columns: 1fr;
	}
	.grid2{
		grid-template-columns: 1fr 1fr;
	}
	.grid3{
		grid-template-columns: 1fr 1fr 1fr;
	}
	.grid4{
		grid-template-columns: 1fr 1fr 1fr 1fr;
	}


	img{
		width: 96%;
		height: 90%;

		border-radius: 5px;
		border-color: rgba(0,0,0,0);

		box-sizing: border-box;

		transition: border 400ms ease-in-out, transform 400ms ease-in-out;

	}
	img:hover{
		border: 1px solid var(--main-border-color);
		transform: scale(1.01);
	}


	@media only screen and (max-width: 999px) {

		.span1{
			grid-column: span 1;
		}
		.span2{
			grid-column: span 2;
		}
		.span3{
			grid-column: span 3;
		}
		.span4{
			grid-column: span 3;
		}

		h4{

			font-size: 1.2em;

		}
		img{
			height: 90%;
		}


	}

	@media only screen and (max-width: 750px) {

		#itemcontainer{
			grid-template-rows: 0.25fr 1.5fr;
		}

		.span1{
			grid-column: span 1;
		}
		.span2{
			grid-column: span 2;
		}
		.span3{
			grid-column: span 2;
		}
		.span4{
			grid-column: span 2;
		}



		#itemGrid{
			min-height: 0px;
		}

		.grid1{
			max-height: 240px !important;
			max-width: 640px;
			display: grid;
			justify-items: center;
		}

		.grid2{

			max-height: 460px;
			grid-template-columns: 1fr 1fr;
			row-gap: 5px;

		}
		.grid3{

			max-height: 460px;
			grid-template-columns: 1fr 1fr;
			row-gap: 5px;

		}
		.grid4{

			max-height: 460px;
			grid-template-columns: 1fr 1fr;
			row-gap: 5px;

		}


		h4{

			font-size: 5vw;

		}

		.grid1 img, .grid2 img{
			height: 60%;
		}
		img{

			width: 100% !important;
		}
	}

</style>
