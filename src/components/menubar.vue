<template>

	<div id="menubar">

		<a href="/">
			<div id="coverImg"></div>
			<h1>BASIS64</h1>
		</a>

		<div id="menuitems" :style="{gridTemplateRows: `repeat(${this.items.length}, auto)`}">


			<p v-on:click="scrollTo(index)" v-for="(item, index) in items" :key="index">
					{{ item }}
			</p>

		</div>

		<a href="mailto:ethan@basis64.nl" target="_blank">
			<div id="email" class="contactButton">ethan@basis64.nl</div>
		</a>
		<a href="https://github.com/EthanHermsey?tab=repositories" target="_blank">
			<div id="git" class="contactButton">EthanHermsey</div>
		</a>

	</div>

</template>

<script>

export default {

	props: {

		items: []

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

		box-shadow:  -1px 0px 10px black;

	}


	a{

		text-decoration: none;
		color: var(--line-color);

	}


	#coverImg{

		margin-left: 10px;
		margin-top: 2vh;
		width: 2.5vw;
		height: 2.5vw;


		border-radius: 50%;
		opacity: 0.5;

		background-image: url('../assets/cover.jpg');
		background-size: cover;
		background-position: center;

		box-shadow:  2px 2px 6px black;

	}

	h1{

		margin: 0;
		margin-top: -1.25em;
		width: 80%;

		font-family: 'EunomiaLight';
		font-weight: 700;
		font-size: 2vw;
		transform: scaleY(1.5);
		text-align: right;
	}

	#menuitems{

		padding-top: 1vh;
		width: 100%;
		height: 83vh;


		display: grid;
		grid-template-columns: 100%;
		grid-template-rows: repeat(28, auto );

		text-transform: capitalize;

	}

	p{

		width: 100%;
		padding-left: 10px;
		margin: 0;

		color: var(--sec-line-color);
		font-size: min( 1.6vh, 1.15vw );
	}

	#menuitems p:hover{
		text-decoration: underline;
		cursor: pointer;
	}


	.contactButton{

		position: fixed;

		padding-right: 10px;
		margin-left: -10px;
		width: 10vw;
		height: 3vh;

		background-color: var(--button-bg-color);

		color: var(--main-bg-color) !important;
		text-align: center;
		font-weight: 700;


		font-size: 0.8vw;
		text-align: right;


		display: grid;
		align-items: center;

		user-select: text !important;
	}

	#email{

		bottom: calc( 3vh + 15px );

	}
	#email::before{
		position: absolute;

		content: '';

		margin-left: 15px;
		height: 3vh;
		width: 3vh;

		background-image: url('../assets/mail.png');
		background-position: center;
		background-size: 80%;
		background-repeat: no-repeat;
	}

	#git{

		bottom: 10px;

	}
	#git::before{
		position: absolute;

		content: '';

		margin-left: 15px;
		height: 3vh;
		width: 3vh;

		background-image: url('../assets/git.png');
		background-position: center;
		background-size: 80%;
		background-repeat: no-repeat;
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

		#coverImg{

			position: fixed;

			margin-left: 1vw;
			margin-top: 5px;
			width: 45px;
			height: 45px;


			border-radius: 50%;
			opacity: 0.5;

			background-image: url('../assets/cover.jpg');
			background-size: cover;
			background-position: center;

		}

		h1{

			position: fixed;

			width: auto !important;

			margin: 0px;
			left: 64px;

			font-size: 45px;
			transform: none;
			float: left;
		}

		#menuitems{

			display: none

		}

		.contactButton{

			position: fixed;

			right: 15px;

			height: 20px;
			width: 16vw;

			font-size: 1.5vw;

		}

		#email{

			top: 2.5px;

		}
		#email::before{
			height: 20px;
			width: 20px;
		}

		#git{

			top: 25px;

		}
		#git::before{
			height: 20px;
			width: 20px;
		}

	}

	@media only screen and (max-width: 750px) {

		#menubar{
			box-shadow: none;
		}

		.contactButton{

			padding-right: 5px;
			margin-left: -5px;
			width: 40vw;

			font-size: 2vw;

		}

	}

</style>
