<template>

	<div id="cardcontainer" v-on:click="hide">

		<div id="card" v-on:click="stopPropagation">

			<div id="closeCard" v-on:click="hide"></div>
			<p id="itemTitle">{{ cardData.title }}</p>
			<img id="itemImage" :src="`./resources/${cardData.image}`">
			<div id="itemTxt">

				<p id="itemDescription">{{ cardData.description }}</p>
				<a id="itemLink" class="cardButton" :href="cardData.link">LIVE</a>
				<a v-if="cardData.video" id="itemVideo" class="cardButton" :href="cardData.video">VIDEO</a>

			</div>

		</div>

  </div>

</template>

<script>

export default {

	props: {

		cardData: Object

	},
	methods: {
		hide() {

			this.$emit( 'hide' );

		},
		stopPropagation( e ) {

			e.stopPropagation();

		}
	}

};

</script>


<style scoped>

	#cardcontainer{

		z-index: 99;
		position: fixed;
		left: 0;
		top: 0;
		width: 100vw;
		height: 100vh;

		backdrop-filter: blur(2px);

	}

	#closeCard{

		position: absolute;
		top: 10px;
		right: 15px;

		width: 42px;
		height: 42px;

		background-image: url('../assets/close.png');
		background-size: cover;
		background-position: center;

	}
	#closeCard:hover{
		transform: scale(1.1);
		cursor: pointer;
	}

	#card{

		position: absolute;

		padding-left: 15px;

		left: 25vw;
		top: 25vh;
		width: 50vw;
		height: 50vh;

		background-color: var(--sec-bg-color);

		color: var(--sec-line-color);
		border-color: var(--sec-border-color);
		border-style: solid;
		border-width: 1px;
		border-radius: 0 2px 2px 0;

		display: grid;
		grid-template-columns: calc(50vw * 0.618) auto;
		grid-template-rows: 12.5% 87.5%;

	}

	#itemTitle{

		margin: 10px;
		font-size: 2em;
		font-family: 'EunomiaLight';
		font-weight: 700;
		color: var(--line-color);

		grid-column: span 2;

	}
	#itemImage{

		width: calc(50vw * 0.618);
		max-height: 40vh;

	}

	#itemTxt{

		height: 100%;

		display: grid;
		grid-template-rows: 65% 15% 15%;

		align-items: center;

	}

	#itemDescription{

		margin-left: 15px;
		padding-left: 5px;

		width: calc(50vw * 0.34 - 10px);
		height: 25vh;

		background-color: rgba(200, 200, 200, 0.05);

		overflow-y: scroll;

	}

	#itemDescription::-webkit-scrollbar{
		width: 2px;
		background: rgba(0,0,0,0);
	}

	.cardButton{

		display: block;

		margin-left: 15px;
		padding-top: 5px;
		padding-bottom: 5px;

		width: calc(50vw * 0.33);

		background-color: var(--button-bg-color);

		color: var(--main-bg-color);
		text-decoration: none;
		text-align: center;
		font-weight: 700;

		border-color: var(--sec-border-color);
		border-style: outset;
		border-width: 2px;

	}
	.cardButton:hover{
		border-color: var(--sec-line-color);
	}
	.cardButton:active{
		border-style: inset;
	}

	@media only screen and (max-width: 999px) {

		#card{

			left: 15vw;
			top: 10vh;
			width: 70vw;
			height: 80vh;

			grid-template-rows: 10% 40% 50%;
			grid-template-columns: 100%;
		}

		#itemDescription{

			margin-left: 12.5px;
			margin-top: 10px;

			width: calc(100% - 50px);

			font-size: 1.25em;

		}

		#itemImage{

			margin-left: -20px;
			width: calc(100% - 20px);

			max-width: 60vh;
			max-height: 98%;

			place-self: center;

		}

		#itemTitle{

			grid-column: span 1;

		}

		.cardButton{
			margin-left: calc( 100% - (50vw * 0.33) - 25px);
		}

	}

	@media only screen and (max-width: 750px) {
		#card{
			position: absolute;

			left: 2.5vw;
			top: 5vh;
			width: 90vw;
			height: 88vh;
		}

		.cardButton{

			display: block;

			margin-left: 0;
			width: 95%;
		}
	}


</style>
